# Search indexes and vector stores

A search index is a derived retrieval structure, not the authority for a document or permission. Choose a store from query patterns: full-text relevance, metadata filters, vector similarity, transactional updates, and rebuild behavior.

## Azure AI Search index design

![Diagram of a vector index with filterable metadata, HNSW nodes, query vectors, and cited readable results.](https://raw.githubusercontent.com/DrHazemAli/enterprise-system-design/main/assets/vector-index-design.png)

```json
{"name":"contentVector","type":"Collection(Edm.Single)","searchable":true,"retrievable":false,"dimensions":1536,"vectorSearchProfile":"hnsw-cosine"}
```

Pair vector fields with human-readable content and filterable metadata such as tenant, document version, language, and ACL revision. Azure AI Search supports HNSW or exhaustive KNN configuration, vector profiles, and optional quantization with rescoring. [Vector index configuration](https://learn.microsoft.com/azure/search/vector-search-how-to-create-index)

## Choice matrix

| Need | Prefer |
|---|---|
| Full text, facets, hybrid ranking, filters, enrichment | Azure AI Search |
| Transactional records with vector adjacency | Relational or document store with vector capability |
| High-speed derived cache | Key-value store |

HNSW trades exactness for lower query cost. Exhaustive KNN is useful as an evaluation baseline. Quantization saves memory but requires relevance testing because compression can change ranking.

## Lifecycle

Index schema changes can require full rebuilds. Keep the source corpus and ingestion manifest so an index can be regenerated. Query results must return human-readable evidence and source identifiers, not raw vectors. [Index update considerations](https://learn.microsoft.com/azure/search/vector-search-how-to-create-index#update-a-vector-index)

## Exercise

Specify an index for policy chunks, including key, text, vector, tenant filter, ACL revision, source version, and vector profile. Explain which schema change forces a rebuild.

## What an index owns

An index owns a query-optimized representation. It does not own the source document, the access decision, or the business record. This matters because a schema can be deleted and rebuilt while the source system remains the authority.

An index converts a query into candidate documents efficiently by maintaining structures that cost storage and write work. Full-text terms, filterable fields, vectors, and facets all create different structures. Add a field because a query or response needs it, not because it might be useful later.

## Schema from actual query paths

For a policy assistant, an index record needs one key, evidence text, metadata used to filter results, and a vector used to rank semantic similarity.

```json
{
	"name": "policy-chunks-v3",
	"fields": [
		{"name": "id", "type": "Edm.String", "key": true, "filterable": true},
		{"name": "tenantId", "type": "Edm.String", "filterable": true},
		{"name": "sourceVersion", "type": "Edm.Int32", "filterable": true},
		{"name": "active", "type": "Edm.Boolean", "filterable": true},
		{"name": "content", "type": "Edm.String", "searchable": true, "retrievable": true},
		{"name": "sourceLocation", "type": "Edm.String", "retrievable": true},
		{"name": "contentVector", "type": "Collection(Edm.Single)", "searchable": true, "retrievable": false, "dimensions": 1536, "vectorSearchProfile": "content-hnsw"}
	]
}
```

The vector field is not a substitute for readable evidence. Azure AI Search recommends storing nonvector text with vectors because chat models use human-readable chunks rather than raw embedding arrays. Vector field dimensions must match the embedding model output, and vector fields are not filterable or sortable. [Azure AI Search vector field design](https://learn.microsoft.com/azure/search/vector-search-how-to-create-index#add-a-vector-field-to-the-fields-collection)

## Ranking choices

HNSW is an approximate nearest-neighbor index. It uses an internal graph to reduce query work, trading a small possibility of missed exact neighbors for lower latency at scale. Exhaustive KNN compares against all vectors and is useful as a relevance baseline, but costs more query work. Treat HNSW parameters and quantization as measurable relevance and capacity settings, not magic defaults.

| Choice | Effect | Validation |
|---|---|---|
| HNSW | lower query cost for large vector sets | compare recall against exhaustive baseline |
| Exhaustive KNN | exact nearest-neighbor reference | use on evaluation sample, not blindly at production scale |
| Scalar or binary quantization | reduces vector memory | measure recall and latency after rescoring |
| Oversampling and rescoring | recovers ranking after compression | measure p95 latency and citation quality |

Azure AI Search supports HNSW and exhaustive KNN vector algorithms plus optional scalar or binary quantization and rescoring. A vector profile binds an algorithm and optional compression to each vector field. [Vector algorithm and profile configuration](https://learn.microsoft.com/azure/search/vector-search-how-to-create-index)

## Query behavior and no-answer policy

Vector search returns the requested $k$ nearest vectors even when they are weak matches. Therefore, a nonempty response is not proof that evidence exists. Use hybrid search, retrieval evaluation, and an explicit no-answer policy.

```http
POST /indexes/policy-chunks-v3/docs/search?api-version=2026-04-01
Content-Type: application/json

{
	"search": "remote worker leave eligibility",
	"filter": "tenantId eq 'tenant-42' and active eq true",
	"select": "content,sourceLocation,sourceVersion",
	"vectorQueries": [{
		"kind": "text",
		"text": "remote worker leave eligibility",
		"fields": "contentVector",
		"k": 50
	}]
}
```

Hybrid retrieval runs keyword and vector paths and fuses their ranked results. For semantic ranking, Azure recommends $k=50$ so the ranker has sufficient candidates. Return selected text and source fields, not raw vectors. [Vector and hybrid query behavior](https://learn.microsoft.com/azure/search/vector-search-how-to-query)

## Access control is query-time work

An ingestion job may copy ACL metadata, but access can change later. Apply the caller's tenant and permission scope to every query, then validate the evidence set before it reaches a prompt. For custom identity models, security filters can trim results using indexed identity strings. Azure AI Search also has native document-level approaches for certain ACL, RBAC, SharePoint, and Purview scenarios; some of those capabilities are preview and have synchronization lag that must be designed explicitly. [Document-level access-control choices](https://learn.microsoft.com/azure/search/search-document-level-access-overview)

The application must distinguish two permissions: its workload identity needs permission to query the index, and the user needs permission to see each returned document. Giving an API `Search Index Data Reader` access does not by itself implement user-level document authorization. [Azure AI Search data-plane roles](https://learn.microsoft.com/azure/search/search-security-rbac)

## Index lifecycle and release process

Schema changes can require a full rebuild, especially changes to existing fields or vector definitions. Keep an ingestion manifest so a new index can be created from source versions rather than copied from a previous index.

1. Create a new versioned index and grant only the required workload roles.
2. Backfill from immutable source versions with the target parser, chunker, and embedding model.
3. Compare record counts, deletion state, metadata completeness, and vector dimensions.
4. Run relevance, security, latency, and load tests against both versions.
5. Shift reads through an alias or application routing decision.
6. Retain the prior version for rollback until its source and retention conditions allow removal.

Azure documents that changes to existing index fields often require drop and full rebuild, while some additions can be made without one. [Vector index update guidance](https://learn.microsoft.com/azure/search/vector-search-how-to-create-index#update-a-vector-index)

## Capacity and observability

Vector memory grows with record count, dimensions, numeric representation, algorithm structure, and replicas. A rough raw-vector estimate before index overhead is:

$$
	ext{vector bytes} = \text{records} \times \text{dimensions} \times 4
$$

For 100 million 1,536-dimensional single-precision vectors, raw values alone are about 572 GiB. This is not a deployment size; HNSW graph data, replicas, metadata, text, compression, and service behavior add capacity requirements. Measure index size with a representative corpus before committing a storage or cost target.

Monitor query latency by query class, result count, filter selectivity, throttling, index size, ingestion failures, vectorization errors, active-versus-inactive source versions, and security-trim rejection rates. A successful search response with the wrong source version or an unauthorized chunk is a correctness incident, not a relevance issue.

## Review checklist

- Can every returned hit display readable evidence, source location, and source version?
- Do vector dimensions, metric, and query embedding model match the index definition?
- Which queries require exact keyword behavior, vector similarity, filters, or all three?
- Has HNSW recall been compared with an exhaustive evaluation baseline?
- Does every query include tenant, active-source, and permission constraints?
- Can the index be rebuilt from authoritative source versions and an ingestion manifest?
- Is the no-answer condition tested with adversarial and irrelevant queries?
