# EAS Defense — OWASP Agentic 2026 evidence map

**Detailed English mapping · evidence reviewed through R48 · 86 internally numbered measures**

[Français](owasp-agentic-2026.md) · [EAS overview](../README.en.md) · [Architecture](architecture.en.md) · [Qualifications](evidence.en.md)

This is Elyne's evidence mapping against the [OWASP Top 10 for Agentic Applications for 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/). The `ASIxx.n` measure IDs and the English measure descriptions below are **Elyne's internal mapping**, not official OWASP recommendation identifiers or OWASP certification. Category labels are English renderings of Elyne's French matrix.

## Reading the results

- **R14 baseline (8 October):** the earlier, delivered Windows candidate's documented map: **9 V / 61 P / 13 R / 3 O**. Its results are historical and are not retroactively changed by later work.
- **Windows laboratory reading (15 October):** a cumulative, multi-release evidence inventory including the signed R45 candidate and bounded R48 checks: **26 V / 47 P / 10 R / 3 O**. R48 used a separate R42/R43 diagnostic profile after the corrected R46 laboratory installer set the allowed-area ACL; it was not a rerun of R45, a new product version, or proof of a commercial installer. The matrix does not establish that every cited older test was rerun on R45.
- **V** = directly observed within the named laboratory scope; **P** = partial technical coverage or a further acceptance test needed; **R** = implementation or acceptance test outstanding; **O** = organizational decision or evidence needed. A V does not mean complete product-wide or customer-wide coverage.
- At least one mitigation is identified in each of the ten categories (**10/10 functional coverage**); this is distinct from **26/86 bounded direct validations**. There is no claim of OWASP endorsement, universal protection, customer deployment, or Linux parity.

The 'Evidence' column lists internal test or report references. `baseline p. n` points to a page of the earlier internal matrix, not to an independent test. These references are for traceability; raw artifacts are not public. Reports and redacted receipts can be made available in an appropriate evaluation. Blank test references mean that the rationale is a design or implementation assessment rather than a named laboratory receipt.

## ASI01 — Goal hijacking

9 mapped measures · 2 V / 5 P / 1 R / 1 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI01.1 | Untrusted natural-language inputs | P | P | Four R10 injection attempts were blocked or quarantined. The clean message in the same batch was also blocked because it lacked an enrolled contract. Without a positive enrolled control, the filter's independent effect remains only partially established. | R10; baseline p. 2 |
| ASI01.2 | Least privilege and approval of sensitive actions | P | V | In R13, Bonsaï's direct write under the LocalService SID was denied and the file stayed intact; the EAS-authorized tool then worked and the repository baseline was restored. This validates only the code path exercised. | R13; baseline p. 2 |
| ASI01.3 | Change control for goals and system instructions | P | P | Cyber monitors declared files. A formal workflow for changes to an agent's goal is still needed. | —; baseline p. 2 |
| ASI01.4 | Review intent changes before effect | P | P | Policy checks and sequence detection exist. Comparison against an approved business goal remains to be added. | —; baseline p. 2 |
| ASI01.5 | Evaluate a signed envelope binding goals and constraints | R | R | Action evidence exists, but a per-cycle signed goal capsule is not implemented. | —; baseline p. 2 |
| ASI01.6 | Control every source of context | P | P | Memory, retrieval, and A2A filters exist; R25 traced one synthetic FTS chunk by ID and hash. Business connectors, customer ingestion, and general provenance still require acceptance testing. | R25; baseline p. 2 |
| ASI01.7 | Log and track goal drift | P | P | Events and sequences are tracked. A stable goal identifier and an approved business baseline are still needed. | —; baseline p. 2 |
| ASI01.8 | Repeat adversarial campaigns and recovery exercises | V | V | Red campaigns were repeated in R12–R14 and R20/R21B. R21B recorded 19/19 defended jobs and 9/52 undetermined steps. An operator's recurring campaign schedule remains to be established. | R14, R20, R21B; baseline p. 2 |
| ASI01.9 | Connect to the insider-threat process | O | O | Ownership, reporting, procedures, and exercises also depend on the deploying organization. | —; baseline p. 2 |

## ASI02 — Tool misuse

8 mapped measures · 4 V / 3 P / 1 R / 0 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI02.1 | Least-privilege profiles per tool and data scope | P | V | In R15, the EAS reader read 69 authorized bytes and received a Windows denial on a canary; R18 bound the call to the Acta identity. The validation covers this tool and profile only. | R15, R18; baseline p. 3 |
| ASI02.2 | Authenticate and approve each sensitive action | P | P | The broker has an internal token and policy checks. A short-lived approval bound to each actual effect remains to be completed. | —; baseline p. 3 |
| ASI02.3 | Isolate executors and filter network egress | R | V | The real code worker in R20/R21 ran under AppContainer and a Job. Network denial had a positive control; a child retained Low integrity and the same SID, while canaries were denied. On the separate R42/R43 laboratory lineage, R48 observed two allowed and two denied file opens after the corrected R46 laboratory installer set the allowed-area ACL. Direct validation remains limited to the qualified worker; not every registered tool is isolated. | R20, R21, R42, R43, R44, R45, R48; baseline p. 3 |
| ASI02.4 | Check intent and parameters before execution | V | V | Pre-effect control was observed on real paths: policy decision, direct denial, tool and applier receipts, and audit correlation during the native Bonsaï R13 test. | R13; baseline p. 3 |
| ASI02.5 | Set budgets and usage limits | P | P | Call quotas exist. Cost and token ceilings, together with persistent budgets, remain to be completed. | —; baseline p. 3 |
| ASI02.6 | Use temporary, session-bound credentials | R | R | Current internal tokens are not single-use capabilities for each invocation. | —; baseline p. 3 |
| ASI02.7 | Resolve tool identity and version unambiguously | P | P | Registry identifiers are exact. Connector versions and hashes still need verification before activation. | —; baseline p. 3 |
| ASI02.8 | Trace tool calls and detect drift | V | V | Red, EAS, and Cyber receipts were correlated and the ledger was verified. R21B still had nine undetermined steps despite 19/19 defended jobs. Complete business-level lineage remains outside this evidence. | R14, R21B; baseline p. 3 |

## ASI03 — Identity and privilege abuse

9 mapped measures · 1 V / 7 P / 0 R / 1 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI03.1 | Restrict rights and duration per task | R | P | R42–R45 observed restricted OS rights under a signed EAS profile, a Low-integrity AppContainer token, targeted denials, and process termination. R48 added two allowed and two denied file opens on the R42/R43 laboratory lineage after the corrected R46 laboratory installer set the allowed-area ACL. Short duration and binding to each individual task were not qualified. | R42, R43, R44, R45, R48; baseline p. 4 |
| ASI03.2 | Separate identities and spaces across sessions | P | P | R13 observed a native Windows identity; Acta and EAS profiles were confined on the R21–R45 clone. Separation across multiple sessions and several customer agents was not demonstrated. | R13, R21, R42, R45; baseline p. 4 |
| ASI03.3 | Authorize every privileged step centrally | P | V | In R24, write, read, check, and run in one Acta conversation passed through ToolBroker and four os_worker audit events; R13 denied the direct route. Direct validation covers the connected code path only. | R13, R24; baseline p. 4 |
| ASI03.4 | Require human approval for privilege elevation | P | P | A durable confinement review exists. Approval of each business-specific elevation remains to be completed. | —; baseline p. 4 |
| ASI03.5 | Bind tokens to identity, audience, purpose, and session | P | P | A2A messages are bound to content, recipient, and session. Tool tokens are not bound to a signed purpose. | —; baseline p. 4 |
| ASI03.6 | Evaluate centralized agent-identity management | O | O | The deploying organization must choose and integrate AD, Entra, or another identity system in its acceptance environment. | —; baseline p. 4 |
| ASI03.7 | Scope and revoke rights by resource, purpose, and duration | P | P | The registry and persistent revocation exist. Context changes and expiration per task remain to be completed. | —; baseline p. 4 |
| ASI03.8 | Detect privilege delegation | P | P | A2A contracts and checks exist. Delegation chains on a target deployment remain to be exercised. | —; baseline p. 4 |
| ASI03.9 | Detect elevation and out-of-context token reuse | P | P | A2A impersonation and replay signals exist. IAM telemetry and device-code-type flows have not been accepted in a target environment. | —; baseline p. 4 |

## ASI04 — Agentic supply chain

9 mapped measures · 2 V / 6 P / 1 R / 0 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI04.1 | Track provenance, SBOM/AIBOM, and attestations | P | P | Dependencies are pinned and audited. An attested SBOM/AIBOM for the delivered package remains to be produced. | —; baseline p. 5 |
| ASI04.2 | Allow approved sources and verify before installation | P | P | R45 verified and applied a signed laboratory candidate. A product installer that natively rejects an unauthorized source has not been qualified; this remains partial. | R45; baseline p. 5 |
| ASI04.3 | Use reproducible and isolated builds | R | R | Signing and application of a laboratory candidate were observed. An independently reproduced, bit-for-bit identical build has not been attested, and a commercial installer remains unqualified. | R45; baseline p. 5 |
| ASI04.4 | Review and version instructions and schemas | P | P | Configuration and code are versioned. The deploying organization's review workflow remains to be formalized. | —; baseline p. 5 |
| ASI04.5 | Use mutual authentication and signed messages | P | V | In a real TLS trial, an approved client certificate was accepted and a certificate from another CA was denied. R11 accepted a complete hybrid A2A proof and denied missing signatures. Customer PKI and certificate-to-agent binding remain open. | local TLS tests, R11; baseline p. 5 |
| ASI04.6 | Continuously check components and behavior | P | V | In R12, the active Cyber service detected and quarantined the exact Red canary at the same SHA-256 hash. R35 also correlated an HPKE rejection. Direct validation covers those monitored objects. | R12, R35; baseline p. 5 |
| ASI04.7 | Pin versions, deploy progressively, and roll back | P | P | Monitored files and bounded restoration exist. A progressive-deployment pipeline remains to be established. | —; baseline p. 5 |
| ASI04.8 | Revoke a compromised component quickly | P | P | Tool and session confinement and token revocation exist. Distribution of revocations across multiple hosts has not been accepted. | —; baseline p. 5 |
| ASI04.9 | Tolerate compromise of one component | P | P | R35 installed Cyber under LocalService; R36B observed 18 denied opens across nine EAS secrets. Inherited handles, indirect routes, and multi-host failures remain open. | R35, R36B; baseline p. 5 |

## ASI05 — Unexpected code execution

7 mapped measures · 2 V / 5 P / 0 R / 0 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI05.1 | Validate outputs and proposed code | V | V | R13 observed a real mediated code write and denial of a direct write; local CodeShield tests analyzed hostile diffs. An end-to-end link covering the same diff remains outside the evidence. | R13, local CodeShield tests; baseline p. 6 |
| ASI05.2 | Separate the agent from production systems | R | P | R21/R22 confined the tested Acta service and denied direct access to EAS secrets; R42–R45 qualified signed EAS profiles. No customer or production deployment, nor an entire third-party agent, was qualified. | R21, R22, R42, R45; baseline p. 6 |
| ASI05.3 | Prohibit unsafe code evaluators | P | P | The lint tool does not run the code. All business-specific executors still need to be inventoried and checked. | —; baseline p. 6 |
| ASI05.4 | Use an unprivileged account and isolated environment | P | P | Low-integrity AppContainer and Job were observed for selected workers and profiles, including the R48 process with allowed and denied file accesses. R37 also found an active Administrators group in the laboratory client's token; a generally unprivileged account is not proven. | R21, R37, R42, R45, R48; baseline p. 6 |
| ASI05.5 | Separate sessions and generation from execution | P | P | R21–R25 exercised a confined Acta ASGI profile; R42–R45 provided a generic EAS launcher. Isolation of every session and process remains to be accepted. | R21, R23, R42, R45; baseline p. 6 |
| ASI05.6 | Approve and allowlist executions | P | P | A registry and review of sensitive areas exist. Approvals for elevated executions remain to be added. | —; baseline p. 6 |
| ASI05.7 | Apply static analysis, monitoring, and execution traces | V | V | The native P0-04 test in R13 provided the Windows SID, tool and applier receipts, EAS audit events, and baseline restoration for the connected code agent. | R13; baseline p. 6 |

## ASI06 — Memory and context poisoning

9 mapped measures · 2 V / 4 P / 3 R / 0 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI06.1 | Encrypt data and minimize data access | P | P | mTLS and EAS decisions exist; R37–R40 isolated an Acta-specific Store under a separate OS identity. At-rest encryption and ACLs for every agent store were not qualified. | R37, R40; baseline p. 7 |
| ASI06.2 | Check content before writing | V | V | P0-03 passed in a native R13 trial with the real Bonsaï agent: adversarial memory/retrieval writes were submitted to EAS, with effective identity and restoration verified. | R13; baseline p. 7 |
| ASI06.3 | Segment memory and contexts | P | P | R13 validated a real memory path; R40 persisted an Acta exchange through a separate Store. Multi-tenant segmentation and coverage of all agents were not demonstrated. | R13, R40; baseline p. 7 |
| ASI06.4 | Authenticate sources and limit retention | P | P | The internal-token boundary exists. Retention policies by sensitivity remain to be added. | —; baseline p. 7 |
| ASI06.5 | Track provenance and detect anomalous writes | P | P | R25 traced a synthetic FTS chunk from retrieval to the EAS filter by ID and SHA-256. Cryptographic provenance of a customer corpus was not demonstrated. | R25; baseline p. 7 |
| ASI06.6 | Prevent automatic re-ingestion as trusted content | R | R | Explicit control over re-ingestion of agent output remains to be implemented. | —; baseline p. 7 |
| ASI06.7 | Quarantine, recover, and review risky memory | V | V | R13 denied a hostile write before persistence and verified return to a clean baseline; local tests cover quarantine and snapshots. Review and recovery of a real store already contaminated were not demonstrated. | R13, local MemoryShield tests; baseline p. 7 |
| ASI06.8 | Expire unverified memory | R | R | Time-to-live and automatic purging for each unverified entry remain to be implemented. | —; baseline p. 7 |
| ASI06.9 | Gate retrieval on provenance and validity | R | R | R25 followed a preloaded FTS chunk, but did not gate sensitive retrieval on authenticated provenance and validity or TTL. The measure remains to be implemented. | R25; baseline p. 7 |

## ASI07 — Inter-agent communications

9 mapped measures · 5 V / 3 P / 1 R / 0 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI07.1 | Encrypt channels and authenticate peers mutually | P | V | A real laboratory TLS connection accepted an approved client certificate and rejected missing certificates or certificates from another CA. Agent identity, rotation, and deployment PKI remain open. | local TLS tests; baseline p. 8 |
| ASI07.2 | Protect content and context integrity | P | V | R12/R14 denied altered HPKE ciphertext or context, with audit and Cyber correlation for the targeted trial. The overall P0-02 gate remained INCONCLUSIVE. | R12, R14; baseline p. 8 |
| ASI07.3 | Bind anti-replay to context and time | P | V | R10–R12 observed one acceptance of a concurrent nonce, rejection of an exact replay, and rejection of an authentic token after 3,604 seconds. Task windows and the overall P0-02 gate remain open. | R10, R11, R12; baseline p. 8 |
| ASI07.4 | Reject weak modes and check capabilities | P | V | R11/R12 denied an incomplete hybrid proof and a downgraded HPKE mode while accepting the complete control. Direct validation covers only the modes tested, without an exhaustive customer registry. | R11, R12; baseline p. 8 |
| ASI07.5 | Reduce leakage through traffic metadata | R | R | Message-size padding and rate or timing shaping have not been implemented. | —; baseline p. 8 |
| ASI07.6 | Version protocols and negotiate compatible capabilities | P | P | Schemas are strict and the signing domain is versioned. Profile negotiation between peers remains to be added. | —; baseline p. 8 |
| ASI07.7 | Authenticate discovery and routing | P | P | The local registry has no public enrollment. Federated discovery has not been deployed. | —; baseline p. 8 |
| ASI07.8 | Attest registries and agent cards | P | P | Public keys are pinned locally. Signed agent cards and an attestation chain remain to be added. | —; baseline p. 8 |
| ASI07.9 | Use typed contracts and an explicit audience | P | V | The server enforces the audience and rejects out-of-schema client fields; wrong HPKE recipients and altered signed messages are rejected. Interoperability between third-party stacks was not tested. | R12, local A2A tests; baseline p. 8 |

## ASI08 — Cascading failures

10 mapped measures · 4 V / 4 P / 2 R / 0 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI08.1 | Design for component unavailability | P | V | In R14, audit storage at zero free bytes caused a fail-closed audit_unavailable denial and Cyber alert; recovery and chain verification followed restoration. Distributed failures were not tested. | R14; baseline p. 9 |
| ASI08.2 | Isolate, segment, and restrict interfaces | P | V | R23 isolated Acta through AppContainer/IPC and denied one targeted direct network flow. R35/R36B denied Cyber 18 opens of nine EAS secrets. Direct validation is limited to the paths exercised. | R23, R35, R36B; baseline p. 9 |
| ASI08.3 | Use temporary authorization per sensitive call | R | R | Single-use, task-bound tool capabilities remain to be implemented. | —; baseline p. 9 |
| ASI08.4 | Keep policy independent of the planner | V | V | P0-05 demonstrated an independent defense plane. R35 observed the real Cyber service under LocalService while EAS was stopped and restarted. | R14, R35; baseline p. 9 |
| ASI08.5 | Check results before propagation | P | P | Filtering and review decisions exist. Authorization to propagate business results remains to be completed. | —; baseline p. 9 |
| ASI08.6 | Limit request rates and monitor anomalies | P | P | In local tests, the 21st call was denied after a quota of 20, and a repeated sequence raised RUNAWAY_LOOP. No native VM receipt ties this rate or effect to a real agent. | local tests; baseline p. 9 |
| ASI08.7 | Bound impact and provide a cutoff | P | V | P0-06 observed Cyber quarantining the enrolled Red canary at the same hash and restoring state. R45 stopped one observed parent and child. Scope is limited to those objects and PIDs. | R12, R45; baseline p. 9 |
| ASI08.8 | Monitor behavioral and governance drift | P | P | A sequence monitor exists. A long-term business baseline remains to be established. | —; baseline p. 9 |
| ASI08.9 | Replay traces in isolation before extending policy | R | R | A change-validation pipeline replaying business traces remains to be established. | —; baseline p. 9 |
| ASI08.10 | Sign traces and preserve action lineage | P | P | EAS receipts were correlated; R40 related three Acta Store mutations to seven EAS decisions. The EAS ledger does not certify the whole Acta SQLite database or every propagation. | R40; baseline p. 9 |

## ASI09 — Human trust manipulation

9 mapped measures · 1 V / 6 P / 1 R / 1 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI09.1 | Require explicit approval for sensitive operations | P | P | In a local TestClient test, an exact confirmation and simulated operator were required to release confinement. No human operator or native VM effect was tested on this path. | local tests; baseline p. 10 |
| ASI09.2 | Maintain tamper-evident records | V | V | Native P0-09 in R14 failed closed at zero free bytes, raised a Cyber alert, preserved chain continuity, and detected four mutations in isolated copies. Evidence is limited to those trials. | R14; baseline p. 10 |
| ASI09.3 | Detect exposure and sensitive actions | P | P | Filters and a monitor exist. Coverage of every conversation and connector remains to be completed. | —; baseline p. 10 |
| ASI09.4 | Let users report suspicious interactions | R | R | A user reporting flow with hold and review remains to be implemented. | —; baseline p. 10 |
| ASI09.5 | Adapt trust to risk and train users | P | P | Risk-based decisions exist. Visual risk cues and a training program remain to be established. | —; baseline p. 10 |
| ASI09.6 | Verify provenance and block out-of-scope actions | P | P | Capability checks and action evidence were strengthened by R13/R14 campaigns. Provenance for every recommendation remains to be added. | R13, R14; baseline p. 10 |
| ASI09.7 | Separate preview from effect | P | P | A local TestClient test returned a no-effect GET preview and required an authenticated POST bound to the exact hash before changing state. No native VM user journey was qualified. | local tests; baseline p. 10 |
| ASI09.8 | Assess security usability with operators | O | O | Operator journeys, risk cues, and human evaluation must be developed with the deploying organization. | —; baseline p. 10 |
| ASI09.9 | Detect deviations from approved workflows | P | P | Sequences are monitored. Approved business workflows and deviations from them remain to be defined. | —; baseline p. 10 |

## ASI10 — Rogue agent

7 mapped measures · 3 V / 4 P / 0 R / 0 O in the laboratory reading.

| Internal ID | Measure | R14 | Lab | Evidence-based qualification and remaining limit | Evidence |
| --- | --- | :---: | :---: | --- | --- |
| ASI10.1 | Govern and trace interactions and actions | P | V | R13 exercised real Bonsaï memory and code routes, with pre-effect denials and correlated traces; R40 added one Acta turn and its EAS decisions. Direct validation covers these connected interactions. | R13, R40; baseline p. 11 |
| ASI10.2 | Define trust zones and restrictive isolation | P | V | R23 confined the Acta service, shim, and child, with targeted canary and flow denials; R43/R44 repeated denials under a signed EAS profile. In the separate R42/R43 laboratory setup, R48 observed two permitted and two denied file opens after the corrected R46 installer set the allowed-area ACL, without a manual change to that ACL during R48. Other agents and routes were not qualified. | R23, R43, R44, R48; baseline p. 11 |
| ASI10.3 | Monitor anomalies and collusion | P | P | EAS sequences and Cyber autonomy were demonstrated under failure or load. Real multi-agent collusion was not demonstrated. | —; baseline p. 11 |
| ASI10.4 | Stop, revoke, and quarantine quickly | P | V | P0-06 demonstrated native quarantine. In R45, EAS /stop was followed by verified disappearance of one parent and its child. The exact Job identity and other agent routes remain INCONCLUSIVE. | R12, R45; baseline p. 11 |
| ASI10.5 | Attest identity and sign behavioral manifests | P | P | Hybrid A2A authentication exists. A signed manifest of each agent's goals and tools remains to be added. | —; baseline p. 11 |
| ASI10.6 | Attest periodically and protect keys | P | P | Cyber runs under LocalService and was denied direct opens of EAS secrets in R35/R36B. Indirect handles or copies and HSM/KMS protection were not qualified. | R35, R36B; baseline p. 11 |
| ASI10.7 | Reintegrate from a trusted baseline | P | P | P0-10 reboot/recovery and R13/R14 restorations were verified. Full agent re-attestation before reintegration remains to be specified. | R13, R14; baseline p. 11 |

## Scope and traceability notes

1. The R14 column transcribes the earlier French rev.3 matrix. The Lab column follows the review dated 15 October 2026, supplemented by the bounded R48 file-access result without changing any status. It is a mapping of mitigations and evidence, not a claim that 86 measures were exercised end to end on one build.
2. R12–R14, R20/R21B, and R23–R48 refer to different campaigns and laboratory iterations. Results involving Acta, Bonsaï, or Cyber retain their stated component and route boundaries. Acta's own ledger does not attest the state of all agents or replace the EAS ledger.
3. The internal P0 gate matrix and this 86-measure map use different denominators. A bounded direct validation can coexist with an overall INCONCLUSIVE gate. Historical FAIL and INCONCLUSIVE receipts are not rewritten by a later bounded pass.
4. Windows AppContainer, Job, ACL, and network-denial observations are specific to the laboratory clone and profiles tested. The exact EAS Job identity, GUI-denial attribution, all descendants, an entire unrelated third-party agent, and a commercial installation remained outside the demonstrated scope.
5. The Linux port has separate portability and laboratory evidence. No Windows sandbox result here is transferred to Linux.

**Source basis:** Elyne's French rev.3 matrix (8 October 2026) and internal rev.5 evidence review (15 October 2026), against the OWASP framework linked above. This document is a redacted English restatement; original reports and raw receipts are not embedded.
