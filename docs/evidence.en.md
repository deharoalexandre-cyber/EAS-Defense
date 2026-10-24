# Qualifications: redacted summary

[Français](evidence.md) · [Home](../README.en.md)

This document summarizes laboratory observations without publishing raw receipts, laboratory paths, security configuration, internal rules, or offensive procedures. **A qualification belongs to its tested version and scope.** The results below cannot be added together into a global score.

| Reference | Observed effect | Limit of conclusion |
| --- | --- | --- |
| **R43 — Windows laboratory clone** | Direct file-canary access was denied from an AppContainer probe; the canary was unchanged after the test. | Targeted denial, not proof that every file access is confined. |
| **R44 — Windows laboratory clone** | A targeted connection was denied from the confined process; a positive connectivity control was performed. | Does not establish denial for every network destination or path; attribution to the exact Windows component remains limited. |
| **R45 — Windows laboratory clone** | A child process retained its AppContainer identity; its termination was verified when EAS stopped the managed process. | Does not qualify every process tree lifecycle or a complete third-party agent. |
| **R48 — Windows laboratory clone** | Two allowed file accesses and two denied opens were observed on the R42/R43 lineage after the corrected R46 laboratory installer set the ACLs, without a manual change to the allowed area during R48. | Depends on the tested ACLs and resource; this was not an R45 replay or a qualification of the commercial installer. |
| **P0-05 — R10** | Elyne Cyber remained active after the EAS service stopped. | Earlier test, not replayed on R45; not proof of complete OS privilege independence. |
| **Red R21B — earlier Windows clone** | 19/19 jobs classified as “defended”; 43/52 steps defended and 9 undetermined. | The 9 steps are not PASS. This campaign does not qualify R45. |

Initial trials classified **INCONCLUSIVE** remain so; later scoped observations do not retroactively turn them into PASS. Independent identification of the exact EAS Job, attribution of some Windows initialization denials, and full confinement of a complete third-party agent remain to be qualified.

Windows **R45** remains the reference for assisted technical evaluation. The **Linux** port is still undergoing laboratory qualification.

Detailed evidence can be reviewed during an assisted evaluation after a disclosure review. [Contact Elyne Corp](mailto:admin@elynecorp.fr?subject=EAS%20Defense%20evaluation) · [Public overview](https://elynecorp.com/eas-defense.html).
