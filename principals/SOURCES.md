# Sources and evidence ledger

This ledger records the evidence model for Hazem's Principals. It does not replace inline citations. Each factual claim remains linked at the point where a chapter teaches or applies it.

## Claim hierarchy

The chapters use sources in this order:

1. Normative standards and specifications for protocol, representation, identity, and conformance behavior.
2. Original or peer-reviewed research for algorithms, failure mechanisms, and empirical findings.
3. Official vendor documentation for implementation-specific behavior, constraints, and operational controls.
4. Hazem Ali's publications for the attributed principal, cross-layer synthesis, and engineering method.
5. Derived practice for a design recommendation inferred from the verified mechanism and Hazem's principal.

A derived practice is not presented as a requirement of the source unless the source makes that requirement explicit.

## Hazem Ali research corpus

The collection is organized around five supplied primary author sources:

- Hazem Ali, [The Hidden Boundaries of Modern AI](https://techcommunity.microsoft.com/blog/educatordeveloperblog/the-hidden-boundaries-of-modern-ai/4522995), Microsoft Tech Community, 2026. This supplies the representation-contract, authority-gradient, context-promotion, output-admission, and zero-trust-executor synthesis.
- Hazem Ali, [The Hidden Memory Architecture of LLMs](https://techcommunity.microsoft.com/blog/educatordeveloperblog/the-hidden-memory-architecture-of-llms/4485367), Microsoft Tech Community, 2026. This supplies the memory-first serving model, KV state, admission, paging, determinism, and multi-tenant memory synthesis.
- Hazem Ali, [AI Didn't Break Your Production, Your Architecture Did](https://techcommunity.microsoft.com/blog/educatordeveloperblog/ai-didn%E2%80%99t-break-your-production-%E2%80%94-your-architecture-did/4482848), Microsoft Tech Community, 2026. This supplies the production control-plane, runtime governance, idempotency, containment, and consequence-oriented operating model.
- Hazem Ali, [The Silent Collapse](https://drhazemali.com/blog/the-silent-collapse-deep-stack-hardware-software-failure-modes), 2026. This supplies the execution-capsule, cross-layer correctness, silent-corruption, plan-hash, topology-fingerprint, and fleet-change governance synthesis.
- Hazem Ali, [From Silicon to Pixels](https://drhazemali.com/blog/from-silicon-to-pixels-why-no-ai-agent-can-ship-a-production-browser), 2026. This supplies the verification-dominant engineering, assumption-of-compromise, system-invariant, and AI-under-engineering-supervision synthesis.

## Engineering foundations

- Leslie Lamport, [Proving the Correctness of Multiprocess Programs](https://lamport.azurewebsites.net/pubs/proving.pdf), IEEE Transactions on Software Engineering, 1977. Used for state, safety, and liveness reasoning.
- Nancy Leveson, [Engineering a Safer World](https://mitpress.mit.edu/9780262533690/engineering-a-safer-world/), MIT Press, 2011. Used for system safety, unsafe control actions, and interaction-level constraints.
- Nancy Leveson and Clark Turner, [An Investigation of the Therac-25 Accidents](https://doi.org/10.1109/MC.1993.274940), IEEE Computer, 1993. Used for system-level failure and unsafe interaction analysis.
- Lisanne Bainbridge, [Ironies of Automation](https://doi.org/10.1016/0005-1098(83)90046-8), Automatica, 1983. Used for human oversight and skill-degradation analysis.
- John C. Knight and Nancy G. Leveson, [An Experimental Evaluation of the Assumption of Independence in Multiversion Programming](https://doi.org/10.1109/TSE.1986.6312924), IEEE Transactions on Software Engineering, 1986. Used for common-mode failure and diversity limits.

## Distributed and mission-critical systems

- John D. C. Little, [A Proof for the Queuing Formula: L = lambda W](https://doi.org/10.1287/opre.9.3.383), Operations Research, 1961. Used for queueing and concurrency reasoning.
- Jeffrey Dean and Luiz Andre Barroso, [The Tail at Scale](https://doi.org/10.1145/2408776.2408794), Communications of the ACM, 2013. Used for tail-latency analysis.
- Matt Welsh, David Culler, and Eric Brewer, [SEDA](https://doi.org/10.1145/502034.502057), SOSP, 2001. Used for staged admission and overload control.
- Hector Garcia-Molina and Kenneth Salem, [Sagas](https://doi.org/10.1145/38713.38742), ACM SIGMOD, 1987. Used for long-lived transactions and compensation.
- Algirdas Avizienis et al., [Basic Concepts and Taxonomy of Dependable and Secure Computing](https://doi.org/10.1109/TDSC.2004.2), IEEE Transactions on Dependable and Secure Computing, 2004. Used for dependable-system terminology.

## Cybersecurity standards

- NIST, [SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final). Used for policy decision and enforcement concepts and resource-centered trust.
- NIST, [SP 800-218: Secure Software Development Framework](https://csrc.nist.gov/pubs/sp/800/218/final). Used for secure development and supply-chain practices.
- NIST, [SP 800-53 Rev. 5](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final). Used for control families and evidence expectations.
- Unicode Consortium, [UAX #9: Unicode Bidirectional Algorithm](https://unicode.org/reports/tr9/). Used for logical order, display order, and bidirectional controls.
- Unicode Consortium, [UTS #39: Unicode Security Mechanisms](https://www.unicode.org/reports/tr39/). Used for confusable, mixed-script, and identifier-security mechanisms.
- Chromium, [Threat Model and Defenses Against Compromised Renderers](https://chromium.googlesource.com/chromium/src/+/main/docs/security/compromised_renderers.md). Used for assumption-of-compromise and receiving-side validation patterns.
- [SLSA specification](https://slsa.dev/spec/v1.2/) and [The Update Framework security model](https://theupdateframework.io/security/). Used for provenance, artifact verification, and update-system threat analysis.

## AI systems research

- Ashish Vaswani et al., [Attention Is All You Need](https://arxiv.org/abs/1706.03762), 2017. Used for Transformer attention and token-state foundations.
- Patrick Lewis et al., [Retrieval-Augmented Generation](https://arxiv.org/abs/2005.11401), 2020. Used for parametric generation conditioned on retrieved non-parametric memory.
- Nils Reimers and Iryna Gurevych, [Sentence-BERT](https://arxiv.org/abs/1908.10084), 2019. Used for sentence embeddings and similarity retrieval.
- Jeff Johnson, Matthijs Douze, and Herve Jegou, [Billion-scale similarity search with GPUs](https://arxiv.org/abs/1702.08734), 2017. Used for numerical vector-search mechanisms.
- Tri Dao et al., [FlashAttention](https://arxiv.org/abs/2205.14135), 2022. Used for input/output-aware attention and memory-movement analysis.
- Woosuk Kwon et al., [Efficient Memory Management for Large Language Model Serving with PagedAttention](https://arxiv.org/abs/2309.06180), 2023. Used for KV-cache paging and serving utilization.
- Ari Holtzman et al., [The Curious Case of Neural Text Degeneration](https://arxiv.org/abs/1904.09751), 2019. Used for decoding-policy effects on visible output.
- PyTorch, [Reproducibility documentation](https://docs.pytorch.org/docs/stable/notes/randomness.html), and NVIDIA, [cuBLAS reproducibility documentation](https://docs.nvidia.com/cuda/cublas/index.html#results-reproducibility). Used for conditional determinism and execution-envelope constraints.

## Reliability and observability

- W3C, [Trace Context](https://www.w3.org/TR/trace-context/). Used for cross-service trace propagation.
- OpenTelemetry, [Trace specification](https://opentelemetry.io/docs/specs/otel/trace/), and [Generative AI semantic conventions](https://github.com/open-telemetry/semantic-conventions-genai). Used for trace, span, event, metric, and AI telemetry models.
- Open Compute Project, [AI Silent Data Corruption at Scale](https://www.opencompute.org/documents/ocp-wp-sdc-in-ai-20240814-pdf), 2024. Used for silent-corruption risk and fleet-level detection framing.
- NVIDIA, [Dynamic Page Retirement](https://docs.nvidia.com/deploy/dynamic-page-retirement/index.html). Used for observable GPU memory remediation state and recovery constraints.
- NIST, [SP 800-61 Rev. 2: Computer Security Incident Handling Guide](https://csrc.nist.gov/pubs/sp/800/61/r2/final), and [SP 800-160 Vol. 2 Rev. 1](https://csrc.nist.gov/pubs/sp/800/160/v2/r1/final). Used for incident response and cyber-resilient system design.

## Microsoft-specific verification

Azure and Microsoft Foundry claims are verified inline against current Microsoft Learn pages. The recurring source families are:

- [Microsoft Foundry observability](https://learn.microsoft.com/en-us/azure/ai-foundry/concepts/observability)
- [Foundry agent tracing](https://learn.microsoft.com/en-us/azure/ai-foundry/observability/concepts/trace-agent-concept)
- [Azure Monitor Application Insights](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)
- [Azure AI Search hybrid search](https://learn.microsoft.com/en-us/azure/search/hybrid-search-overview)
- [Azure role-based access control](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview)
- [Azure Kubernetes Service security concepts](https://learn.microsoft.com/en-us/azure/aks/concepts-security)

Product documentation can change. Chapters cite the specific behavior where it is used and should be re-fetched before material revision.

## Generated instructional image record

All images were generated with the existing Azure deployment `gpt-image-2-1`. No deployment was created, changed, deleted, scaled, or redeployed.

| Asset | Purpose | Chapter use |
|---|---|---|
| `assets/hazem-ali-boundary-first-engineering.png` | Teach representation, authority, isolation, consequence, evidence, and recovery boundaries | All five `principals/engineering/` chapters |
| `assets/hazem-ali-mission-critical-control-loop.png` | Teach contain, preserve, recover, validate, resume, and evidence-gate relationships | All five `principals/mission-critical-systems/` chapters |
| `assets/hazem-ali-zero-trust-ai-execution.png` | Teach model-as-proposer, policy decision, enforcement, isolation, and kill-switch flow | All five `principals/cybersecurity/` chapters |
| `assets/hazem-ali-ai-representation-memory-admission.png` | Teach input representation, retrieval promotion, KV serving state, decoding, and admission | All five `principals/ai-systems/` chapters |
| `assets/hazem-ali-execution-evidence-incident-control.png` | Teach execution capsules, drift checks, consequence SLOs, and incident controls | All five `principals/reliability-and-operations/` chapters |

Every generated bitmap includes the visible in-image credit `Credits: Hazem Ali`. Every chapter includes the same visible Markdown credit immediately below its image reference.