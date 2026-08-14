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

The collection is organized around the supplied primary author sources and Hazem Ali's coauthored security research:

- Hazem Ali, [The Hidden Boundaries of Modern AI](https://techcommunity.microsoft.com/blog/educatordeveloperblog/the-hidden-boundaries-of-modern-ai/4522995), Microsoft Tech Community, 2026. This supplies the representation-contract, authority-gradient, context-promotion, output-admission, and zero-trust-executor synthesis.
- Hazem Ali, [The Hidden Memory Architecture of LLMs](https://techcommunity.microsoft.com/blog/educatordeveloperblog/the-hidden-memory-architecture-of-llms/4485367), Microsoft Tech Community, 2026. This supplies the memory-first serving model, KV state, admission, paging, determinism, and multi-tenant memory synthesis.
- Hazem Ali, [AI Didn't Break Your Production, Your Architecture Did](https://techcommunity.microsoft.com/blog/educatordeveloperblog/ai-didn%E2%80%99t-break-your-production-%E2%80%94-your-architecture-did/4482848), Microsoft Tech Community, 2026. This supplies the production control-plane, runtime governance, idempotency, containment, and consequence-oriented operating model.
- Hazem Ali, [The Silent Collapse](https://drhazemali.com/blog/the-silent-collapse-deep-stack-hardware-software-failure-modes), 2026. This supplies the execution-capsule, cross-layer correctness, silent-corruption, plan-hash, topology-fingerprint, and fleet-change governance synthesis.
- Hazem Ali, [From Silicon to Pixels](https://drhazemali.com/blog/from-silicon-to-pixels-why-no-ai-agent-can-ship-a-production-browser), 2026. This supplies the verification-dominant engineering, assumption-of-compromise, system-invariant, and AI-under-engineering-supervision synthesis.
- Hazem Ali, [The Hidden Architecture of Nano Architectures](https://techcommunity.microsoft.com/blog/educatordeveloperblog/the-hidden-architecture-of-nano-architectures/4493391), Microsoft Tech Community, 2026. This supplies the executed-plan, runtime-regime, finite-precision, memory-hierarchy, fabric, and security-performance coupling synthesis.
- Hazem Ali et al., [LAAF: Logic-layer Automated Attack Framework](https://arxiv.org/abs/2603.17239), arXiv preprint, 2026. This supplies the six-stage LPCI red-teaming model, persistent stage breaker, OWASP risk mapping, experimental results, and explicit threats-to-validity boundaries.
- Hazem Ali et al., [Building an Auditable Security Layer for Agentic AI](https://techcommunity.microsoft.com/blog/educatordeveloperblog/building-an-auditable-security-layer-for-agentic-ai/4495753), Microsoft Tech Community, 2026. This supplies the context, capability, evidence, retrieval, and detection gates used for auditable agent authority.

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

## Networking standards

- IETF, [RFC 1034: Domain Names, Concepts and Facilities](https://www.rfc-editor.org/rfc/rfc1034), [RFC 1035: Domain Names, Implementation and Specification](https://www.rfc-editor.org/rfc/rfc1035), and [RFC 4033: DNS Security Introduction and Requirements](https://www.rfc-editor.org/rfc/rfc4033). Used for Domain Name System hierarchy, resolution, caching, delegation, message behavior, and DNS Security Extensions scope.
- IETF, [RFC 1122: Requirements for Internet Hosts](https://www.rfc-editor.org/rfc/rfc1122), [RFC 8200: Internet Protocol, Version 6](https://www.rfc-editor.org/rfc/rfc8200), and [RFC 8201: Path MTU Discovery for IP version 6](https://www.rfc-editor.org/rfc/rfc8201). Used for host behavior, best-effort packet delivery, IPv6 forwarding, fragmentation, and path maximum transmission unit discovery.
- IETF, [RFC 1918: Address Allocation for Private Internets](https://www.rfc-editor.org/rfc/rfc1918), [RFC 3022: Traditional IP Network Address Translator](https://www.rfc-editor.org/rfc/rfc3022), and [RFC 4787: Network Address Translation Behavioral Requirements for UDP](https://www.rfc-editor.org/rfc/rfc4787). Used for private addressing, translation state, port mapping, and NAT traversal constraints.
- IETF, [RFC 9293: Transmission Control Protocol](https://www.rfc-editor.org/rfc/rfc9293), [RFC 5681: TCP Congestion Control](https://www.rfc-editor.org/rfc/rfc5681), and [RFC 3168: Explicit Congestion Notification](https://www.rfc-editor.org/rfc/rfc3168). Used for reliable byte-stream behavior, flow control, congestion response, retransmission, and explicit congestion signals.
- IETF, [RFC 8446: TLS 1.3](https://www.rfc-editor.org/rfc/rfc8446), [RFC 9000: QUIC](https://www.rfc-editor.org/rfc/rfc9000), and [RFC 9002: QUIC Loss Detection and Congestion Control](https://www.rfc-editor.org/rfc/rfc9002). Used for secure transport, handshake and replay boundaries, multiplexed streams, loss recovery, and congestion control.
- IETF, [RFC 9110: HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110), [RFC 9113: HTTP/2](https://www.rfc-editor.org/rfc/rfc9113), and [RFC 9114: HTTP/3](https://www.rfc-editor.org/rfc/rfc9114). Used for request semantics, authority, status codes, retries, multiplexing, and application mapping over TCP or QUIC.
- IETF, [RFC 2328: OSPF Version 2](https://www.rfc-editor.org/rfc/rfc2328) and [RFC 4271: Border Gateway Protocol 4](https://www.rfc-editor.org/rfc/rfc4271). Used for link-state routing, adjacency, flooding, shortest-path calculation, interdomain reachability, path attributes, and policy-based route selection.

## Cybersecurity standards

- NIST, [SP 800-207: Zero Trust Architecture](https://csrc.nist.gov/pubs/sp/800/207/final). Used for policy decision and enforcement concepts and resource-centered trust.
- NIST, [SP 800-218: Secure Software Development Framework](https://csrc.nist.gov/pubs/sp/800/218/final). Used for secure development and supply-chain practices.
- NIST, [SP 800-53 Rev. 5](https://csrc.nist.gov/pubs/sp/800/53/r5/upd1/final). Used for control families and evidence expectations.
- NIST, [SP 800-161 Rev. 1](https://csrc.nist.gov/pubs/sp/800/161/r1/upd1/final). Used for malicious functionality, vulnerable components, and cybersecurity supply-chain risk boundaries.
- NIST, [AI 100-2 E2023: Adversarial Machine Learning](https://csrc.nist.gov/pubs/ai/100/2/e2023/final). Used for evasion, poisoning, privacy, trojan, and backdoor terminology without treating taxonomy as proof of a proposed exploit.
- MITRE ATT&CK, [T1078 Valid Accounts](https://attack.mitre.org/techniques/T1078/). Used for compromised-credential access, persistence, privilege escalation, and defense-evasion mechanisms.
- Unicode Consortium, [UAX #9: Unicode Bidirectional Algorithm](https://unicode.org/reports/tr9/). Used for logical order, display order, and bidirectional controls.
- Unicode Consortium, [UAX #15: Unicode Normalization Forms](https://www.unicode.org/reports/tr15/). Used for canonical and compatibility normalization behavior in identity processing.
- Unicode Consortium, [UTS #39: Unicode Security Mechanisms](https://www.unicode.org/reports/tr39/). Used for confusable, mixed-script, and identifier-security mechanisms.
- IETF, [RFC 3986: Uniform Resource Identifier Generic Syntax](https://www.rfc-editor.org/rfc/rfc3986) and [RFC 9110: HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110). Used for URI normalization, origin authority, method semantics, and representation boundaries.
- Chromium, [Threat Model and Defenses Against Compromised Renderers](https://chromium.googlesource.com/chromium/src/+/main/docs/security/compromised_renderers.md). Used for assumption-of-compromise and receiving-side validation patterns.
- Linux, [seccomp system call](https://man7.org/linux/man-pages/man2/seccomp.2.html) and [Seccomp BPF documentation](https://www.kernel.org/doc/html/latest/userspace-api/seccomp_filter.html), together with Docker, [Docker Engine security](https://docs.docker.com/engine/security/). Used for syscall filtering, namespaces, control groups, capabilities, and container isolation boundaries.
- OWASP, [LLM01: Prompt Injection](https://genai.owasp.org/llmrisk/llm01-prompt-injection/) and [LLM06: Excessive Agency](https://genai.owasp.org/llmrisk/llm062025-excessive-agency/). Used as a risk taxonomy for separating untrusted instruction influence from excessive action authority.
- [SLSA Build Track](https://slsa.dev/spec/v1.2/build-track-basics), [SLSA artifact verification](https://slsa.dev/spec/v1.2/verifying-artifacts), and [The Update Framework security model](https://theupdateframework.io/security/). Used for provenance levels, trusted-builder and digest verification, and update-system threat analysis.

## AI systems research

- Ashish Vaswani et al., [Attention Is All You Need](https://arxiv.org/abs/1706.03762), 2017. Used for Transformer attention and token-state foundations.
- Patrick Lewis et al., [Retrieval-Augmented Generation](https://arxiv.org/abs/2005.11401), 2020. Used for parametric generation conditioned on retrieved non-parametric memory.
- Nils Reimers and Iryna Gurevych, [Sentence-BERT](https://arxiv.org/abs/1908.10084), 2019. Used for sentence embeddings and similarity retrieval.
- Jeff Johnson, Matthijs Douze, and Herve Jegou, [Billion-scale similarity search with GPUs](https://arxiv.org/abs/1702.08734), 2017. Used for numerical vector-search mechanisms.
- Tri Dao et al., [FlashAttention](https://arxiv.org/abs/2205.14135), 2022. Used for input/output-aware attention and memory-movement analysis.
- Woosuk Kwon et al., [Efficient Memory Management for Large Language Model Serving with PagedAttention](https://arxiv.org/abs/2309.06180), 2023. Used for KV-cache paging and serving utilization.
- Zhaorun Chen et al., [AgentPoison: Red-teaming LLM Agents via Poisoning Memory or Knowledge Bases](https://arxiv.org/abs/2407.12784), 2024. Used for sparse, trigger-dependent poisoning of persistent agent memory and RAG knowledge bases under the paper's stated attacker assumptions and experimental limits.
- Ari Holtzman et al., [The Curious Case of Neural Text Degeneration](https://arxiv.org/abs/1904.09751), 2019. Used for decoding-policy effects on visible output.
- PyTorch, [Reproducibility documentation](https://docs.pytorch.org/docs/stable/notes/randomness.html), and NVIDIA, [cuBLAS reproducibility documentation](https://docs.nvidia.com/cuda/cublas/index.html#results-reproducibility). Used for conditional determinism and execution-envelope constraints.

## Reliability and observability

- Google, [Service Level Objectives](https://sre.google/sre-book/service-level-objectives/), [Alerting on SLOs](https://sre.google/workbook/alerting-on-slos/), and [Canarying Releases](https://sre.google/workbook/canarying-releases/). Used for service-level indicators and objectives, error budgets, multi-window burn-rate alerts, and canary evaluation.
- Google, [Incident Response](https://sre.google/workbook/incident-response/) and [Postmortem Culture](https://sre.google/workbook/postmortem-culture/). Used for incident roles, communication, coordination, blameless analysis, and durable corrective learning.
- W3C, [Trace Context](https://www.w3.org/TR/trace-context/). Used for cross-service trace propagation.
- OpenTelemetry, [Trace specification](https://opentelemetry.io/docs/specs/otel/trace/), and [Generative AI semantic conventions](https://github.com/open-telemetry/semantic-conventions-genai). Used for trace, span, event, metric, and AI telemetry models.
- Open Compute Project, [AI Silent Data Corruption at Scale](https://www.opencompute.org/documents/ocp-wp-sdc-in-ai-20240814-pdf), 2024. Used for silent-corruption risk and fleet-level detection framing.
- NVIDIA, [Dynamic Page Retirement](https://docs.nvidia.com/deploy/dynamic-page-retirement/index.html). Used for observable GPU memory remediation state and recovery constraints.
- Google Project Zero, [Exploiting the DRAM Rowhammer bug to gain kernel privileges](https://projectzero.google/2015/03/exploiting-dram-rowhammer-bug-to-gain.html), 2015. Used only for demonstrated CPU DDR3 DRAM disturbance and privilege-escalation mechanisms. It is not used as evidence of a GPU HBM or KV-cache exploit.
- Zhenkai Zhang et al., [Invalidate+Compare: A Timer-Free GPU Cache Attack Primitive](https://www.usenix.org/conference/usenixsecurity24/presentation/zhang-zhenkai), USENIX Security 2024. Used for demonstrated cache-activity leakage on studied NVIDIA Ampere and Ada Lovelace systems. It is not used as evidence of memory writes or KV-cache corruption.
- NIST, [SP 800-61 Rev. 3: Incident Response Recommendations and Considerations for Cybersecurity Risk Management](https://csrc.nist.gov/pubs/sp/800/61/r3/final), and [SP 800-160 Vol. 2 Rev. 1](https://csrc.nist.gov/pubs/sp/800/160/v2/r1/final). Used for incident response and cyber-resilient system design.

## Microsoft-specific verification

Azure and Microsoft Foundry claims are verified inline against current Microsoft Learn pages. The recurring source families are:

- [Microsoft Foundry observability](https://learn.microsoft.com/en-us/azure/foundry/concepts/observability)
- [Foundry agent tracing](https://learn.microsoft.com/en-us/azure/foundry/observability/concepts/trace-agent-concept)
- [Foundry agent evaluation](https://learn.microsoft.com/en-us/azure/foundry/observability/how-to/evaluate-agent)
- [Azure Monitor Application Insights](https://learn.microsoft.com/en-us/azure/azure-monitor/app/app-insights-overview)
- [Azure AI Search hybrid search](https://learn.microsoft.com/en-us/azure/search/hybrid-search-overview)
- [Azure role-based access control](https://learn.microsoft.com/en-us/azure/role-based-access-control/overview)
- [Managed identities for Azure resources](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview)
- [Microsoft Entra Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [Azure Policy](https://learn.microsoft.com/en-us/azure/governance/policy/overview)
- [Azure Kubernetes Service security concepts](https://learn.microsoft.com/en-us/azure/aks/concepts-security)
- [Azure Availability Zones](https://learn.microsoft.com/en-us/azure/reliability/availability-zones-overview)
- [Azure Well-Architected disaster recovery](https://learn.microsoft.com/en-us/azure/well-architected/reliability/disaster-recovery)
- [Azure Architecture Center Throttling pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/throttling)
- [Azure Architecture Center Queue-Based Load Leveling pattern](https://learn.microsoft.com/en-us/azure/architecture/patterns/queue-based-load-leveling)
- [Azure Backup](https://learn.microsoft.com/en-us/azure/backup/backup-overview)
- [IOMMU-based GPU isolation](https://learn.microsoft.com/en-us/windows-hardware/drivers/display/iommu-based-gpu-isolation)

Product documentation can change. Chapters cite the specific behavior where it is used and should be re-fetched before material revision.

## Instructional Image Record


| Asset | Purpose | Chapter use |
|---|---|---|
| `assets/hazem-ali-boundary-first-engineering.png` | Teach representation, authority, isolation, consequence, evidence, and recovery boundaries | All five `principals/engineering/` chapters |
| `assets/hazem-ali-mission-critical-control-loop.png` | Teach contain, preserve, recover, validate, resume, and evidence-gate relationships | All five `principals/mission-critical-systems/` chapters |
| `assets/hazem-ali-zero-trust-ai-execution.png` | Teach model-as-proposer, policy decision, enforcement, isolation, and kill-switch flow | Cybersecurity chapters `01` through `06` |
| `assets/hazem-ali-ai-representation-memory-admission.png` | Teach input representation, retrieval promotion, KV serving state, decoding, and admission | All five `principals/ai-systems/` chapters |
| `assets/hazem-ali-network-path-evidence.png` | Teach naming, route selection, forwarding, secure transport, congestion, policy, and path-evidence boundaries | All five `principals/networking/` chapters |
| `assets/hazem-ali-execution-evidence-incident-control.png` | Teach execution capsules, drift checks, consequence SLOs, and incident controls | All five `principals/reliability-and-operations/` chapters |
| `assets/hazem-ali-dormant-agent-memory-poisoning.png` | Distinguish valid authentication, bounded write authorization, provenance, delayed retrieval influence, action authority, policy enforcement, and backend receipts | `principals/cybersecurity/06-auditable-agent-authority-and-lifecycle-red-teaming.md` |
| `assets/hazem-ali-kv-byte-integrity-propagation.png` | Show how one changed byte can affect tensor payload, quantization metadata, block identity, or ownership while keeping Rowhammer evidence scoped to CPU DDR DRAM | `principals/cybersecurity/07-kv-cache-integrity-and-silent-hardware-corruption.md` |

