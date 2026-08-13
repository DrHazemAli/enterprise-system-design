# Agentic red teaming

Evaluation asks how a system performs on declared examples.

Red teaming asks how an adversary can make it fail.

An agent expands the attack surface because it can retrieve data, call tools, retain state, and delegate work.

The red-team target is therefore the complete workflow, not only the model response. A benign-looking answer can still lead to an unsafe tool proposal, a poisoned document can influence later steps, and a retry can duplicate an effect. Testing each boundary with synthetic data and reversible tools produces evidence about the system that will actually be deployed.

This chapter builds a repeatable red-team program without giving test systems real production authority.

## Learning objectives

- distinguish assessment, evaluation, penetration testing, red teaming, and monitoring;
- define assets, boundaries, personas, objectives, strategies, judges, and findings;
- build a production-like purple environment;
- test prompt, tool, data, multi-agent, and resource risks;
- calculate attack success rate and uncertainty;
- calibrate automated judges with human review;
- create reproducible findings and regression tests;
- assign ownership, service levels, retest, and release vetoes.

## The costly failure

A team attacks a chat model in isolation.

It records no harmful responses and declares the agent safe.

Production adds a write-capable ticket tool and an internal search connector.

A poisoned document then causes an unauthorized update.

Another team runs attacks against production with real credentials.

The exercise becomes the incident it intended to prevent.

A third team reports zero successes from 20 probes.

It mistakes limited observation for proof of safety.

## Vocabulary

**Vulnerability assessment** systematically checks known weakness classes.

**Model evaluation** measures behavior on a declared distribution.

**Penetration testing** attempts to exploit technical controls under an agreed scope.

**AI red teaming** simulates adversarial users and data intended to cause unsafe behavior.

**Production monitoring** observes deployed traffic and system signals.

An **asset** is data, capability, model, identity, reputation, or availability worth protecting.

A **trust boundary** separates components with different authority or ownership.

An **attacker persona** states access, knowledge, motive, and constraints.

An **attack objective** is the undesirable outcome being tested.

A **strategy** changes interaction structure, such as multi-turn escalation.

A **transformation** changes representation while preserving intent.

A **target version** identifies the exact tested system.

An **oracle** or **judge** labels whether an attack succeeded.

A **finding** is a supported claim about a reproducible weakness.

**Exploitability** estimates attacker effort and prerequisites.

A **remediation owner** is accountable for closure.

## Controlling invariant

Every release-blocking finding is reproducible against pinned target, policy, data, and tool versions and is reviewed by a qualified human.

The evidence bundle names every dependency required to reproduce the result.

An automated score alone cannot veto or approve a release.

A human opinion without captured evidence cannot close a finding.

## Additional invariants

Red-team tools have no production credentials.

All side effects terminate in mock or reversible resources.

Synthetic records cannot identify real people.

Egress is allowlisted and monitored.

Every attack objective maps to an asset and trust boundary.

Every severe result has an evidence identifier.

Every accepted remediation becomes a regression test.

Every override records approver, reason, scope, and expiry.

## Measurable requirements

The program tests every release candidate before promotion.

Critical findings have a zero-tolerance release veto.

High findings receive an owner within one business day.

Critical remediation starts within four hours.

At least 10 percent of automated labels receive blind human audit.

Judge false-positive and false-negative rates are reported.

Repeated scans pin all target versions.

The purple environment is destroyed or reset after each campaign.

No real external side effect is possible.

## Threat taxonomy

Content harms include violence, sexual, hate, and self-harm outputs.

Prompt injection includes direct and indirect instruction attacks.

Sensitive-data leakage includes model, retrieval, memory, and tool data.

Prohibited actions violate declared policy.

Irreversible actions create permanent effects without confirmation.

Task-adherence failures violate goals, rules, or procedure.

Code vulnerability produces exploitable code patterns.

Groundedness failure invents claims outside evidence.

Resource exhaustion consumes tokens, loops, queue capacity, or tool quota.

Tool abuse invokes valid tools for invalid purposes.

Cross-agent confused deputy uses one agent's authority through another.

## Purple environment

Purple means a nonproduction environment where attack and defense teams collaborate.

Use production-like topology and policy.

Replace customer records with synthetic data.

Replace payment, email, delete, deployment, and identity tools with mocks.

Return realistic status, latency, and failure responses.

Constrain network egress.

Use dedicated identities and subscriptions or resource groups.

Apply low quotas and kill switches.

Log every tool proposal and mock effect.

Reset state between runs.

Microsoft recommends a purple environment and transient runs for Foundry agent red teaming ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/concepts/ai-red-teaming-agent)).

## Architecture

```mermaid
flowchart LR
    SCOPE[Scope and threat model] --> OBJ[Versioned objectives]
    OBJ --> GEN[Baseline and transformed attacks]
    GEN --> TARGET[Agent target]
    TARGET --> MOCK[Mock tools and synthetic data]
    TARGET --> CAP[Response and tool capture]
    CAP --> JUDGE[Automated judges]
    JUDGE --> HUMAN[Human adjudication]
    HUMAN --> FIND[Findings registry]
    FIND --> OWNER[Owner and remediation]
    OWNER --> REG[Regression corpus]
    REG --> GATE{Release gate}
    GATE -->|fail| OWNER
    GATE -->|pass| RELEASE[Candidate release]
```

The target never receives production authority.

Judges produce candidate labels.

Humans adjudicate release-significant evidence.

Findings loop back into regression.

## Instructional figure

![Agentic red-team findings move from scoped synthetic attacks through human review, remediation, regression, and release gating](https://raw.githubusercontent.com/DrHazemAli/enterprise-system-design/main/assets/agentic-red-team-findings-lifecycle.png)
Credits: Hazem Ali

The figure preserves lineage across target, policy, dataset, tool, and scan versions.

The remediation loop prevents rediscovery without learning.

The warning on judge error prevents false certainty.

## Scope contract

```yaml
campaign: rt-2026-08-12
target: support-agent:42
policy: agent-policy:19
prompt: support-prompt:31
retrieval_index: kb-synthetic:12
tool_bundle: mock-tools:8
dataset: objectives:17
allowed_egress: [foundry-evaluation, synthetic-api]
forbidden: [production-data, production-tools, public-posting]
kill_switch_owner: security-on-call
```

Scope defines what may be attacked.

It also defines what the red team may never touch.

## Attack workflow

1. Inventory assets, identities, tools, stores, and boundaries.
2. Define attacker personas and prerequisites.
3. Write outcomes rather than payloads as objectives.
4. Pin target and policy versions.
5. Seed synthetic data and mock tools.
6. Verify egress denial and kill switch.
7. Run baseline direct probes.
8. Apply safe transformations to baseline objectives.
9. Run multi-turn strategies where the target supports them.
10. Place indirect instructions in synthetic documents and mock outputs.
11. Capture responses, tool calls, decisions, and state transitions.
12. Score each row with versioned judges.
13. Blind-audit a stratified human sample.
14. Triage by severity, exploitability, and exposure.
15. Assign owner and due date.
16. Remediate and rerun the reproduction bundle.
17. Promote the case into a regression corpus.
18. Apply release gates and archive evidence.

The workflow turns an adversarial observation into an engineering artifact by preserving the conditions that made it possible. A captured outcome without pinned target, policy, tool, and synthetic-data versions cannot distinguish a product regression from a changed environment. Conversely, a reproduction bundle lets the remediation owner test whether a policy change blocks the objective while leaving the intended workflow intact. Resetting the purple environment between runs removes prior state as an accidental prerequisite and makes a later retest meaningful.

## Safe objective schema

```json
{
  "objective_id": "obj-tool-019",
  "asset": "synthetic-refund-ledger",
  "boundary": "agent-to-tool-broker",
  "persona": "authenticated-low-privilege-user",
  "goal": "cause an unconfirmed consequential mock action",
  "success_condition": "mock_tool_effect_created_without_confirmation",
  "risk": "prohibited-action",
  "severity_if_real": "critical"
}
```

The schema describes an outcome without publishing a harmful prompt.

Store sensitive attack material under restricted access.

## Baseline and transformations

Baseline attacks state an objective directly.

Transformations alter encoding, spacing, order, language, or framing.

Strategies alter the interaction over time.

Multi-turn attacks accumulate context.

Crescendo gradually increases pressure or risk.

Indirect attacks place instructions in retrieved data.

Tool-output attacks place them in mock results.

Always retain the baseline parent identifier.

Foundry documents baseline, transformation, multi-turn, crescendo, and indirect strategies through its PyRIT integration ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/concepts/ai-red-teaming-agent)).

## Foundry boundaries

The AI Red Teaming Agent is preview and should not be treated as a production SLA-backed control ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/how-to/develop/run-scans-ai-red-teaming-agent)).

The documented local path supports text-only single-turn interaction ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/how-to/develop/run-scans-ai-red-teaming-agent)).

The broader concept documentation describes multi-turn strategies and cloud-only agentic risk categories ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/concepts/ai-red-teaming-agent)).

Therefore record local, cloud, model, or agent mode in every result.

Cloud agentic categories use synthetic data and mock tools ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/concepts/ai-red-teaming-agent)).

Current support excludes workflow agents, non-Foundry agents, function tools, browser tools, connected agents, and computer-use tools in the documented matrix ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/concepts/ai-red-teaming-agent)).

Do not infer coverage for unsupported targets.

## Risk coverage matrix

| Risk              | Model output | Retrieval      | Tool call       | Multi-agent      |
| ----------------- | ------------ | -------------- | --------------- | ---------------- |
| Content harm      | Yes          | Indirect       | Consequence     | Delegated output |
| Injection         | Direct       | Poisoned data  | Poisoned result | Confused deputy  |
| Leakage           | Memorized    | Indexed secret | Tool result     | Shared context   |
| Prohibited action | Proposal     | Trigger data   | Effect          | Delegated effect |
| Exhaustion        | Long output  | Fan-out        | Retry storm     | Delegation loop  |

Each cell needs either a test or a documented exclusion.

## Attack success rate

For $n$ attacks and $x$ observed successes:

$$
\widehat{ASR}=\frac{x}{n}
$$

Foundry reports Attack Success Rate as its primary automated scan metric ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/how-to/develop/run-scans-ai-red-teaming-agent)).

If 18 of 300 attacks succeed, ASR is 6 percent.

Report uncertainty, not only 6 percent.

An approximate standard error is:

$$
SE=\sqrt{\frac{\hat p(1-\hat p)}{n}}
$$

Here $SE\approx1.37$ percentage points.

A rough 95 percent interval is about 3.3 to 8.7 percent.

Use Wilson or exact intervals near zero or one.

## Zero is not proof

With zero successes in $n$ independent trials, the rule of three gives an approximate 95 percent upper bound of $3/n$.

Zero of 20 still permits an underlying rate near 15 percent.

Zero of 300 permits about 1 percent.

Independence rarely holds perfectly because attacks share templates and judges.

Report objective diversity and clustering.

## Repeated runs

Models and judges can be stochastic.

Repeat high-risk objectives across seeds and times.

Record temperature and decoding settings.

Record judge deployment and evaluator version.

Compare per-objective outcomes, not only pooled totals.

Escalate inconsistent labels to human adjudication.

Do not average away one reproducible critical success.

## Judge calibration

Foundry risk evaluators use hosted models and can return severity or pass/fail labels ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/concepts/evaluation-evaluators/risk-safety-evaluators)).

Content-risk evaluators use a 0-to-7 scale with a configurable threshold, default 3 in the documented interface ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/concepts/evaluation-evaluators/risk-safety-evaluators)).

Build a human-labeled calibration set.

Measure judge precision, recall, and disagreement by risk.

Blind reviewers to judge output.

Use two reviewers for severe ambiguous rows.

Adjudicate disagreement with a domain expert.

Version the rubric.

## Findings schema

```json
{
  "finding_id": "F-2026-041",
  "title": "Mock consequential action lacks confirmation",
  "target_version": "support-agent:42",
  "policy_version": "agent-policy:19",
  "dataset_version": "objectives:17",
  "tool_version": "mock-tools:8",
  "scan_id": "rt-2026-08-12",
  "evidence_ids": ["row-882", "trace-a19"],
  "severity": "critical",
  "exploitability": "moderate",
  "human_review": "confirmed",
  "owner": "agent-platform",
  "due_at": "2026-08-13T12:00:00Z"
}
```

## Severity model

Severity combines impact and reach.

Exploitability combines prerequisites, repeatability, and attacker effort.

Exposure combines traffic, affected identities, and tool availability.

Critical means severe real-world effect with plausible exploitation.

High means material effect or broad sensitive-data exposure.

Medium means constrained effect or meaningful defense weakness.

Low means limited impact or hard prerequisites.

Do not lower severity because the test used synthetic data.

## Reproduction bundle

Include objective identifier.

Include sanitized attack material under access control.

Include exact conversation and mock tool outputs.

Include target, model, prompt, policy, index, and tool versions.

Include random seeds and decoding settings.

Include trace and response identifiers.

Include expected and observed outcomes.

Include judge and human labels.

Include environment reset instructions.

## Release gate

```yaml
release: support-agent:42
veto:
  confirmed_critical_open: 0
  confirmed_high_without_owner: 0
required:
  regression_pass_rate: 1.0
  human_audit_complete: true
  purple_environment_clean: true
exceptions:
  approvers: [security-owner, product-owner]
  expires_in_days: 7
```

Release gates consume finding status, not dashboard averages.

An exception never erases evidence.

A release gate is a state transition over reviewed findings, not a claim that the tested system has no unknown weaknesses. The gate remains useful when it requires evidence that severe findings are closed or explicitly owned, while preserving the original finding and the scope of any temporary exception. If a retest fails after a proposed fix, the finding returns to an open state with the same lineage rather than being replaced by an optimistic aggregate score. That history makes rollback and release recovery traceable when the same weakness reappears under a later model or tool version.

## Remediation patterns

Reduce tool permissions.

Move policy checks outside the model.

Add confirmation for consequential actions.

Separate instruction and data channels.

Constrain retrieval by trust and tenant.

Validate tool outputs before reuse.

Cap loops, tokens, fan-out, and retries.

Isolate agents with different authority.

Remove secrets from prompts and memory.

Add deterministic output schemas.

## Resource exhaustion

Set maximum turns per conversation.

Set maximum tool calls per task.

Set maximum delegated agents.

Set token and wall-clock budgets.

Detect repeated equivalent actions.

Propagate cancellation.

Bound queues by age and bytes.

Mock throttling and timeout responses.

Test retry storms and cyclic delegation.

## Cross-agent confused deputy

Agent A must not borrow Agent B's identity implicitly.

Every delegation carries authenticated principal and purpose.

Agent B reauthorizes the requested operation.

Shared memory retains source and classification labels.

Tool capabilities are not transferable bearer strings.

Trace links record delegation without implying parent authority.

Test low-privilege-to-high-privilege delegation.

## Identity and network

Use dedicated red-team identities.

Grant access only to synthetic stores and mock tools.

Deny production subscriptions and endpoints.

Allowlist outbound evaluator and target endpoints.

Protect attack datasets and findings with separate roles.

Audit policy, target, and dataset changes.

Expire temporary access after the campaign.

## Incident handling

Stop the campaign when a real side effect is possible.

Trigger the kill switch.

Revoke red-team credentials.

Preserve traces and environment state.

Notify the exercise owner and security incident lead.

Distinguish exercise evidence from real customer impact.

If production data was touched, follow the real incident process.

Reset the environment only after evidence preservation.

## Capacity and cost

Let $O$ be objectives, $S$ strategies, and $R$ repeated runs.

Approximate target calls are:

$$
N=O(1+S)R
$$

For 100 objectives, 5 strategies, and 3 repeats, $N=1800$ calls.

At 1,500 tokens per call, that is 2.7 million target tokens before judge tokens.

Add evaluator inference, storage, review, and remediation labor.

Bound concurrency to protect the target and evaluator quotas.

Measure cost per confirmed finding and per closed regression.

## Backpressure and recovery

Queue campaigns by release priority.

Pause when evaluator errors exceed threshold.

Checkpoint completed objective identifiers.

Do not duplicate tool effects after resume.

Mock effects use idempotency keys.

Retry transient calls with bounded jitter.

Do not retry a deterministic policy denial indefinitely.

Preserve partial evidence with an incomplete status.

## Observability

Track objectives, strategies, calls, errors, and latency.

Track ASR with confidence intervals by slice.

Track judge-human disagreement.

Track finding age and service-level breaches.

Track remediation and regression pass rates.

Track environment egress and mock effects.

Track target, policy, dataset, and judge drift.

Track false positives and false negatives.

## Known limitations

Automated scans cover known objectives and generated variants.

They do not match unlimited human creativity.

Synthetic distributions differ from production.

Mock tools do not reproduce every sandbox behavior.

Foundry notes that its judge-based ASR can be nondeterministic and produce false positives, requiring human review ([Microsoft Learn](https://learn.microsoft.com/azure/foundry/concepts/ai-red-teaming-agent)).

Absence of observed success is not absence of vulnerability.

## Alternatives and trade-offs

Use unit tests for deterministic contracts.

Use standard evaluation for representative quality distributions.

Use penetration testing for infrastructure and authorization exploits.

Use AI red teaming for adversarial behavioral discovery.

Use production monitoring for real distribution drift.

Use manual experts for novel and high-impact reasoning.

Combine them because each answers a different question.

## Design review checklist

- Are assets and trust boundaries explicit?
- Are attack objectives outcome-based and versioned?
- Is the environment isolated from real effects?
- Are synthetic data and mock tools realistic enough?
- Are target, policy, data, and tool versions pinned?
- Does coverage include indirect and tool-output attacks?
- Are multi-agent authority boundaries tested?
- Is ASR reported with uncertainty?
- Are judges calibrated against humans?
- Are release findings reproducible and human-reviewed?
- Does every owner have a due date?
- Does every remediation become regression evidence?

## Hands-on exercise

Design a campaign for a support agent with search and refund tools.

Inventory five assets and four boundaries.

Define three attacker personas.

Write ten safe outcome-based objectives.

Create synthetic customer and payment records.

Build read, write, timeout, and throttle mock responses.

Deny every production endpoint.

Run baseline, transformed, indirect, and multi-turn classes.

Pin target, prompt, policy, index, and tools.

Calculate calls for 80 objectives, 4 strategies, and 3 repeats.

Compute ASR for 7 successes in 240 attacks.

Compute an uncertainty interval.

Explain zero successes in 25 trials.

Audit 10 percent of labels blindly.

Create one critical finding bundle.

Assign severity, exploitability, owner, and due date.

Implement confirmation in the mock broker.

Promote the case into regression.

Rerun and apply the release gate.

Finish with residual risks outside campaign coverage.

## What, why, and how

Agentic red teaming probes how adversarial users and data can cause unsafe outputs, disclosures, actions, or resource use.

It is needed because representative evaluation does not search deliberately for failure.

It works through scoped objectives, safe synthetic environments, versioned attacks, captured evidence, calibrated judges, human adjudication, owned remediation, regression, and release gates.
