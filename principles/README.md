# Hazem's Principles

These principles are by **Hazem Ali**. They codify the system-design techniques, engineering judgments, and production controls that recur across his published research on artificial intelligence, mission-critical systems, cybersecurity, hardware-software correctness, and verification-dominant engineering.

Hazem Ali is a Distinguished Mission-Critical Systems Engineer and Architect, a [Microsoft AI Most Valuable Professional](https://mvp.microsoft.com/en-US/MVP/profile/4865c7ae-cb5b-4eb5-b128-608b1f9a6ebc), and the Founder and Chief Executive Officer of Skytells. His [author profile](https://drhazemali.com/author/hazem-ali) and [Microsoft Tech Community profile](https://techcommunity.microsoft.com/users/hazem/3056729) provide the publication record behind this collection.

This collection turns Hazem Ali's research into a principal-level operating method for architecture reviews, production design, security decisions, and technical leadership.

It is not a generic best-practices catalog. It is an attributed synthesis of Hazem Ali's published and coauthored research, checked against primary standards, vendor documentation, and original research. The collection separates three kinds of statement:

- **Hazem's Principle**: a method or synthesis derived from Hazem's published work.
- **Verified mechanism**: behavior supported by a primary specification, vendor document, or peer-reviewed source.
- **Practice derived here**: an implementation rule inferred from the principle and mechanism. It should be adapted to the system's risk and evidence.

## The method in one sentence

Do not trust the visible artifact. Trust the engineered path that can prove how an object changed representation, scope, authority, execution state, and consequence.

This is the common line across Hazem's work on [hidden AI boundaries](https://techcommunity.microsoft.com/blog/educatordeveloperblog/the-hidden-boundaries-of-modern-ai/4522995), [LLM memory architecture](https://techcommunity.microsoft.com/blog/educatordeveloperblog/the-hidden-memory-architecture-of-llms/4485367), [production AI architecture](https://techcommunity.microsoft.com/blog/educatordeveloperblog/ai-didn%E2%80%99t-break-your-production-%E2%80%94-your-architecture-did/4482848), [silent hardware-software failure](https://drhazemali.com/blog/the-silent-collapse-deep-stack-hardware-software-failure-modes), and [verification-dominant browser engineering](https://drhazemali.com/blog/from-silicon-to-pixels-why-no-ai-agent-can-ship-a-production-browser).

## Collection map

```text
principles/
|-- README.md
|-- SOURCES.md
|-- engineering/
|   |-- 01-boundary-first-system-design.md
|   |-- 02-verification-dominant-engineering.md
|   |-- 03-contracts-invariants-and-state-transitions.md
|   |-- 04-system-level-verification.md
|   `-- 05-evidence-driven-architecture-decisions.md
|-- mission-critical-systems/
|   |-- 01-safe-state-and-failure-containment.md
|   |-- 02-idempotency-and-ambiguous-outcomes.md
|   |-- 03-admission-control-and-backpressure.md
|   |-- 04-redundancy-and-common-mode-failure.md
|   `-- 05-recovery-rehearsal-and-resumption.md
|-- cybersecurity/
|   |-- 01-zero-trust-ai-execution.md
|   |-- 02-canonical-identity-and-representation-security.md
|   |-- 03-capability-scoped-authorization.md
|   |-- 04-isolation-sandboxing-and-untrusted-execution.md
|   |-- 05-supply-chain-and-execution-integrity.md
|   |-- 06-auditable-agent-authority-and-lifecycle-red-teaming.md
|   `-- 07-kv-cache-integrity-and-silent-hardware-corruption.md
|-- ai-systems/
|   |-- 01-representation-authority-and-memory.md
|   |-- 02-retrieval-promotion-and-provenance.md
|   |-- 03-memory-admission-and-serving-state.md
|   |-- 04-determinism-and-execution-envelopes.md
|   `-- 05-generation-termination-and-output-admission.md
|-- networking/
|   |-- 01-packet-path-and-forwarding-evidence.md
|   |-- 02-naming-and-secure-transport.md
|   |-- 03-congestion-overload-and-backpressure.md
|   |-- 04-routing-convergence-and-failure-domains.md
|   `-- 05-zero-trust-network-observability.md
`-- reliability-and-operations/
    |-- 01-consequence-oriented-slos.md
    |-- 02-causal-observability-and-trace-evidence.md
    |-- 03-execution-capsules-and-silent-corruption.md
    |-- 04-governed-change-canaries-and-rollback.md
    `-- 05-incident-command-recovery-and-learning.md
```

## Reading order

1. Begin with [boundary-first system design](engineering/01-boundary-first-system-design.md), then complete the five engineering principles in numeric order.
2. Continue through [mission-critical systems](mission-critical-systems/01-safe-state-and-failure-containment.md) to connect invariants to overload, ambiguous outcomes, containment, and recovery.
3. Use [cybersecurity](cybersecurity/01-zero-trust-ai-execution.md) to bind representation and action to canonical identity, scoped authority, isolation, provenance, auditable agent decisions, and inference-memory integrity.
4. Study [AI systems](ai-systems/01-representation-authority-and-memory.md) to follow the operational object through retrieval, memory, execution, decoding, and admission.
5. Trace [networking](networking/01-packet-path-and-forwarding-evidence.md) from name authority through forwarding, secure transport, overload, routing convergence, policy enforcement, and path evidence.
6. Finish with [reliability and operations](reliability-and-operations/01-consequence-oriented-slos.md) to turn those controls into evidence, service objectives, change gates, and incident practice.

## The six questions

Hazem's method can be used in any architecture review by asking six questions in order:

1. **Object**: What exact object exists at this boundary: bytes, code points, token IDs, vectors, context, logits, decoded text, a tool proposal, or committed state?
2. **Contract**: Which parser, schema, tokenizer, model revision, policy, runtime, or protocol gives that object meaning?
3. **Authority**: What can the object influence now, and did that authority increase at this boundary?
4. **Scope**: Which user, tenant, task, environment, time window, and data classification constrain it?
5. **Evidence**: What record proves the transformation and decision without retaining unnecessary sensitive content?
6. **Recovery**: If the decision is wrong, how is execution stopped, contained, reversed, and learned from?

A design that cannot answer one of these questions has an unspecified boundary. An unspecified boundary is not automatically vulnerable or unreliable, but its behavior cannot yet be defended.

## Practice levels

| Level | Review posture | Required evidence |
|---|---|---|
| Advisory | Output informs a person and has no direct side effect | Input/output identity, source citations, model and prompt version |
| Assisted | Output proposes a bounded operation for confirmation | Advisory evidence plus exact diff, target, policy decision, approver |
| Delegated | Runtime executes reversible, low-impact actions | Capability scope, idempotency, limits, trace, rollback, kill switch |
| Consequential | Runtime can affect money, access, safety, production, or regulated data | Independent verifier, human or deterministic admission, immutable audit, tested containment, named owner |

The model's confidence does not select the level. The consequence and reversibility do.

## Attribution and evidence policy

The collection attributes Hazem's ideas directly and links factual claims at the point of use. [SOURCES.md](SOURCES.md) records the source hierarchy, claim boundaries, and verification status.

The notes do not claim that every practice is mandated by a standard. They distinguish standards from Hazem Ali's architecture method and from implementation guidance derived in this repository.

## Intended audience

These notes are for principal engineers, distinguished engineers, architects, security leaders, platform owners, and senior operators who must decide whether a complex system is safe to release and possible to operate. They assume readers can evaluate trade-offs but do not assume a specific cloud or framework.

The objective is not maximal control. It is explicit control at the boundaries where uncertainty gains authority.