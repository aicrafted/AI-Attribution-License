# AIAL_PROVENANCE_SPEC_v0.1.md

**Status:** Working draft (non-normative / companion spec)  
**Purpose:** Define a provenance declaration scheme that can accompany AIAL without becoming the sole legal engine of the license.

**Important:** This specification is intended as a **documentation and transparency standard**, not as a conclusive legal determination of authorship or copyright status.

---

# 1. Design goals

This spec aims to provide:

- machine-readable provenance hints
- human-readable disclosure
- practical granularity for real repositories
- conservative defaults for mixed / unknown / inherited content
- compatibility with common OSS workflows

This spec does **not** aim to:
- conclusively determine legal authorship
- establish public domain status by label alone
- replace chain-of-title analysis

---

# 2. Provenance model

## Provenance categories

### 2.1 `generated-origin`
Use when the declaring party states that the covered contribution was produced primarily through automated model generation, subject to human selection / curation / integration, and the party intends to attach a special no-claim declaration (if any).

**Important:**  
This label is descriptive. It does not itself prove lack of copyright.

---

### 2.2 `ai-assisted`
Use when the contribution is substantially human-authored but materially assisted by AI systems.

Examples:
- code completion
- generated refactors later heavily edited by a human
- AI-generated scaffolding with substantial human rework

---

### 2.3 `human-authored`
Use when the declaring party states no material AI-generated code contribution is claimed for the covered contribution.

---

### 2.4 `mixed`
Use when the covered artifact contains mixed provenance that cannot be reliably segmented or is not practical to segment.

**Default legal interpretation:** conservative.  
This label should not imply no-claim.

---

### 2.5 `unknown`
Use when provenance cannot be reliably determined.

**Default legal interpretation:** conservative.  
No special permissions should be inferred.

---

### 2.6 `inherited`
Use when the code was imported or adapted from third-party sources under separate or preexisting licensing terms.

**Important:**  
This label must not override the original upstream license.

---

# 3. Scope of declaration

A provenance declaration should always identify its scope.

## Allowed scopes
- `file`
- `directory`
- `generated artifact`
- `release manifest entry`
- `commit / patch series`
- `embedded block` (optional and advanced; not required)

## Recommendation
For v0.1, prefer:
- **file-level**
- **release-manifest-level**
- **generated-artifact-level**

Avoid making block-level segmentation mandatory.

---

# 4. Required principles

## Principle A — Provenance is declarative, not adjudicative
All declarations under this spec are:
- representations by a contributor, originator, or maintainer
- not judicial or statutory findings

## Principle B — Unknown and mixed are first-class states
Do not force false precision.

## Principle C — Absence of metadata means no special inference
If no declaration exists:
- do not infer generated-origin
- do not infer no-claim
- do not infer reduced rights

---

# 5. Suggested metadata fields (AIAL-native)

These are **AIAL-native field names**. They do not require SPDX governance.

## Minimal field set
- `AIAL-Provenance`
- `AIAL-Originator`
- `AIAL-Tool` (optional)
- `AIAL-Scope` (optional if obvious from placement)
- `AIAL-NoClaim` (optional, only where explicitly intended)

---

# 6. Header examples

## 6.1 File-level example — generated-origin
```text
AIAL-Provenance: generated-origin
AIAL-Originator: Nik the Human
AIAL-Tool: Claude Sonnet 4.6
AIAL-NoClaim: yes
License: AIAL-2.0-draft
```

## 6.2 File-level example — ai-assisted
```text
AIAL-Provenance: ai-assisted
AIAL-Originator: Nik the Human
AIAL-Tool: Claude Sonnet 4.6
License: AIAL-2.0-draft
```

## 6.3 File-level example — mixed
```text
AIAL-Provenance: mixed
AIAL-Originator: Nik the Human
License: AIAL-2.0-draft
```

**Interpretation:**  
Mixed provenance does **not** imply `AIAL-NoClaim`.

## 6.4 File-level example — inherited
```text
AIAL-Provenance: inherited
AIAL-Originator: upstream import from ExampleProject
License: Apache-2.0
```

---

# 7. Release manifest format (recommended)

A release manifest is strongly recommended because it scales better than forcing all semantics into file headers.

## Example
```yaml
version: 0.1
release: v2.0.0-beta1
entries:
  - path: src/generated/parser.rs
    provenance: generated-origin
    originator: Nik the Human
    tool: Claude Sonnet 4.6
    no_claim: true
    license: AIAL-2.0-draft

  - path: src/core/router.rs
    provenance: ai-assisted
    originator: Nik the Human
    tool: Claude Sonnet 4.6
    license: AIAL-2.0-draft

  - path: src/vendor/
    provenance: inherited
    source: upstream package imports
    note: original upstream terms apply
```

---

# 8. Interpretation rules

## Rule 1 — `AIAL-NoClaim` is optional and explicit
No no-claim should be inferred merely from:
- `generated-origin`
- `mixed`
- `unknown`

## Rule 2 — `mixed` and `unknown` never imply special legal effect
They are disclosure states only.

## Rule 3 — `inherited` preserves upstream licensing
No declaration under this spec overrides third-party terms.

## Rule 4 — Metadata binds only the declaring party’s representation
It does not extinguish:
- third-party rights
- unknown rights
- rights held by contributors who did not make the declaration

---

# 9. SPDX compatibility note (non-normative)

AIAL may provide optional examples that are syntactically similar to SPDX or can coexist with SPDX-style headers.

However:
- AIAL does **not** require SPDX adoption
- AIAL metadata fields remain valid even if SPDX never changes

This is a compatibility note only.

---

# 10. Recommended future evolution

Potential v0.2 additions:
- structured JSON schema
- manifest validation rules
- git-commit trailer format
- generated-artifact bundle conventions
- REUSE-style companion guidance
