# AIAL — AI-Attribution License

**Status: pre-draft concept exploration. Not ready for use.**

---

## What is this?

AIAL is an attempt to design a permissive software license that allows contributors to make explicit, structured declarations about the AI-assisted or AI-generated origin of their contributions — without pretending to conclusively resolve unsettled questions about AI authorship and copyright.

The goal is not to replace MIT or Apache. The goal is to explore whether a narrow, conservative extension — provenance declarations + an optional contributor-limited no-claim layer — is coherent and useful enough to be worth formalizing.

## The problem being explored

When a contributor uses an AI system to produce a substantial portion of their code, there is currently no standard way to:

- disclose that provenance in a structured, machine-readable form,
- express "to the extent I hold any rights here, I choose not to assert them" without falsely claiming public domain status,
- do any of the above without overreaching on unsettled law.

AIAL v2 is attempting to address this narrowly.

## What AIAL is not

- It does not claim to determine whether AI-generated code is copyrightable.
- It does not declare generated code to be public domain.
- It does not require SPDX changes.
- It is not a restriction on AI training use.

## Repository contents

| File | Description |
|------|-------------|
| [AIAL_LICENSE_v2_SKELETON.md](AIAL_LICENSE_v2_SKELETON.md) | Working skeleton of the license text (not final legal prose) |
| [AIAL_PROVENANCE_SPEC_v0.1.md](AIAL_PROVENANCE_SPEC_v0.1.md) | Companion provenance declaration specification |
| [AIAL_FAQ_FOR_REVIEWERS.md](AIAL_FAQ_FOR_REVIEWERS.md) | FAQ addressing likely misconceptions |

## Architecture (v2 direction)

Three separable layers:

1. **Permissive license core** — intentionally close to MIT/ISC in shape
2. **Provenance declaration layer** — informational, not legally self-executing
3. **Optional no-claim / covenant layer** — contributor-limited, explicit opt-in only

The provenance categories are: `generated-origin`, `ai-assisted`, `human-authored`, `mixed`, `unknown`, `inherited`.

Conservative defaults apply: absence of a declaration implies nothing. `mixed` and `unknown` imply no special legal effect.

## Current status

This is an early-stage conceptual exploration. The skeleton and spec are working drafts used to test whether the architecture is coherent before investing in polished legal text.

An introductory post to the OSI `license-discuss` mailing list is being prepared to gather feedback on the overall direction.

## Author

Nik the human — feedback welcome via issues.
