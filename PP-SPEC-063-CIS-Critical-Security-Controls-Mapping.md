# PP-SPEC-063: Proof of Efficacy Mapping to CIS Critical Security Controls®

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | CIS Critical Security Controls® (CIS Controls®) Version 8.1, Center for Internet Security, Inc. |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how CIS Critical Security Controls® Controls and Safeguards can be bound to Proof Protocol test cases, evidence, and efficacy results.

The CIS Critical Security Controls® (CIS Controls®) are published and maintained by the Center for Internet Security, Inc. (CIS®). Version 8.1 is an iterative update to Version 8 that, among other changes, adds the Govern security function aligned to NIST CSF 2.0. CIS identifies v8.1 as the latest version at the time of writing. This mapping targets **CIS Controls Version 8.1**.

The upstream source remains authoritative for its own requirements, identifiers, terminology, and guidance. This document defines a **Proof Protocol mapping** and does not supersede, reproduce, modify, or certify conformance to the upstream source. Users referring to the CIS Controls SHOULD consult http://www.cisecurity.org/controls/ for the most up-to-date guidance.

## 2. Scope

The CIS Controls supply external context that can identify what should be examined or tested. Version 8.1 is organized into 18 numbered Controls, each containing numbered Safeguards (identifier format such as `1.1`), with each Safeguard assigned to one or more Implementation Groups (IG1, IG2, IG3) and attributed with an asset type and a security function (for example Govern, Identify, Protect, Detect, or Respond). Proof Protocol supplies an independent evidence model for determining what happened during a test and whether a selected control performed as claimed.

Many Safeguards concern inventories, documentation, processes, and governance. Those Safeguards can be referenced by a proof record but are not themselves empirical efficacy claims (see section 4 and rule 9).

Independent witnessing, proof validity, evidence capture, packaging, anchoring, and efficacy semantics are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A framework requirement, criterion, principle, or obligation may identify a condition of interest. A product, architecture, policy, process, or safeguard may claim to satisfy or mitigate that condition. Proof Protocol binds the external context, test, control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

A Proof Protocol result does **not** by itself establish legal, audit, regulatory, or standards conformance unless the applicable authority separately determines that the evidence is sufficient.

## 4. Metric Definitions

Against a defined corpus or test condition, each applicable empirical case is recorded as **blocked**, **detected**, **missed**, or **INVALID** where those verdicts are meaningful.

Relevant measurements can include containment rate, detection rate, miss rate, false-positive rate, robustness under bypass or failure conditions, version-level results, and **INVALID** when required evidence is incomplete or broken.

Not every upstream requirement is empirical. Governance, documentation, organizational, legal, and procedural requirements MUST NOT be converted into efficacy scores merely because they can be referenced by a proof record.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding external context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested conditions.

## 6. Mapping to CIS Controls

Exact upstream identifiers SHOULD be taken from the authoritative version being mapped and recorded in the ProofBundle™. Upstream titles and text SHOULD NOT be copied into the ProofBundle™ unless the upstream terms permit it. This specification does not redefine upstream requirements.

| CIS Controls context | Proof Protocol treatment | Evidence |
|---|---|---|
| Control (Control 1 to Control 18) | Record the Control number and the CIS Controls version as test context. | Requirement metadata |
| Safeguard (identifier format such as `1.1`) | Bind the Safeguard number to one or more test cases where the Safeguard states a testable security outcome. | Proof record; corpus manifest |
| Implementation Group (IG1, IG2, IG3) | Record the Implementation Group selected by the tested organization as scoping context, not as a result. | Test metadata |
| Asset type attribute | Record the asset class under test and bind the specific assets exercised. | Environment descriptor |
| Security function attribute | Use the function to select the applicable measurement: Protect maps to containment, Detect to detection, Respond (and Recover where assigned) to outcome after the condition; Govern and Identify are generally non-empirical. | Proof records; requirement metadata |
| Asserted safeguard implementation | Record the claimed implementation separately from whether it was present, configured, active, and effective. | Control descriptor |
| Safeguard operation | Exercise the defined condition and capture whether the safeguard operated. | Execution evidence |
| Bypass, evasion, or failure condition | Exercise negative, bypass, misuse, or failure cases where applicable. | Robustness evidence |
| Protected outcome | Establish whether the protected asset or objective was preserved when efficacy is claimed. | Target/outcome evidence |
| Governance, inventory, and documentation Safeguards | Reference as non-empirical context; MUST NOT be scored as efficacy. | Requirement metadata |
| System/version context | Bind material system, policy, configuration, and environment versions. | Environment descriptor |
| Evidence export | Package evidence and provenance for independent examination. | ProofBundle |

## 7. Interoperability Rules

1. The authoritative upstream source, edition/version, and applicable identifier SHOULD be recorded.
2. Upstream identifiers and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not upstream certifications, audit opinions, legal determinations, or endorsements.
4. A control's presence, configuration, activation, detection, and efficacy are distinct facts.
5. A policy decision, alert, log entry, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, service, resource, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, policy, control, environment, mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. Non-empirical requirements MUST remain distinguishable from empirically tested efficacy assertions.

## 8. Framework-Agnostic Architecture

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test or examine**. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. An implementation MAY use CIS Controls, another recognized framework, a proprietary threat model, several frameworks simultaneously, or no external framework when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **The CIS Controls supply prioritized safeguard context. Proof Protocol supplies the evidence model for independently examining whether a selected safeguard performed as claimed.**

No affiliation, endorsement, certification, audit opinion, or sponsorship by the Center for Internet Security, Inc. (CIS®) is implied.

## 10. Source Framework, Attribution, and License

The CIS Critical Security Controls® are external work owned by the Center for Internet Security, Inc. (CIS®). CIS®, CIS Critical Security Controls®, and CIS Controls® are marks of the Center for Internet Security, Inc. Names, identifiers, trademarks, Safeguard titles and descriptions, and expressive content remain subject to CIS ownership and terms.

CIS publishes the CIS Controls under the **Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International Public License (CC BY-NC-ND 4.0)**, with additional CIS clarifications: redistribution is permitted for non-commercial purposes only with credit to CIS and a link to the license; modified materials may not be distributed; users referring to the CIS Controls are required to refer to http://www.cisecurity.org/controls/; and commercial use of the CIS Controls is subject to the prior approval of CIS.

This Proof Protocol mapping is independently authored and licensed under **CC BY 4.0**. That license applies only to original Proof Protocol material in this repository. It does not relicense the CIS Controls, which remain under CC BY-NC-ND 4.0 and the CIS terms quoted below, and it grants no rights in CIS material.

Contributors MUST NOT copy Safeguard titles, Safeguard descriptions, Control descriptions, tables, glossary entries, or any other CIS Controls content into this repository. Doing so would redistribute CC BY-NC-ND material inside a CC BY 4.0 work that permits commercial use and adaptation, which the CIS terms do not allow. Reference Control and Safeguard numbers and independently authored descriptions only.

Implementers who use this mapping together with CIS Controls content in a commercial product or service SHOULD determine whether CIS prior approval is required for that use.

### Required attribution

CIS requires credit to CIS, a link to the license, and a reference to http://www.cisecurity.org/controls/ when referring to the CIS Controls. The CIS license notice reads (quoted verbatim from CIS Critical Security Controls® Version 8.1, section "Creative Commons License"; CIS Controls download: https://www.cisecurity.org/controls/v8-1):

> This work is licensed under a Creative Commons Attribution-NonCommercial-No Derivatives 4.0 International Public License (the link can be found at https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode). To further clarify the Creative Commons license related to the CIS Controls® content, you are authorized to copy and redistribute the content as a framework for use by you, within your organization and outside of your organization, for non-commercial purposes only, provided that (i) appropriate credit is given to CIS, and (ii) a link to the license is provided. Additionally, if you remix, transform, or build upon the CIS Controls, you may not distribute the modified materials. Users of the CIS Controls framework are also required to refer to (http://www.cisecurity.org/controls/) when referring to the CIS Controls in order to ensure that users are employing the most up to date guidance. Commercial use of the CIS Controls is subject to the prior approval of the Center for Internet Security, Inc. (CIS®).

Attribution as provided in this specification:

> CIS Critical Security Controls® (CIS Controls®) Version 8.1, Center for Internet Security, Inc. (CIS®). Licensed under CC BY-NC-ND 4.0 (https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode). For the most up-to-date guidance, refer to http://www.cisecurity.org/controls/. CIS®, CIS Critical Security Controls®, and CIS Controls® are marks of the Center for Internet Security, Inc.

**What this specification reproduces:** the framework name, version, Control and Safeguard numbers and numbering format, Implementation Group designations (IG1, IG2, IG3), and the names of the security function attribute values as structural terms, together with short independently authored factual statements. **What it does not reproduce:** Control titles or descriptions, Safeguard titles or descriptions, tables, mappings, or any other CIS Controls content. Because no CIS content is copied, redistributed, remixed, or adapted, the NoDerivatives and NonCommercial conditions of CC BY-NC-ND 4.0 are not triggered by this repository, and the CC BY 4.0 license of this repository does not extend to any CIS material.

## 11. Versioning

This mapping is versioned independently of CIS Controls. Material upstream changes SHOULD trigger a mapping review and, where necessary, a new version identifying the upstream revision mapped.

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*
