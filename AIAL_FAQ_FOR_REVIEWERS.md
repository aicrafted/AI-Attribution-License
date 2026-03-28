# AIAL_FAQ_FOR_REVIEWERS.md

**Status:** Working reviewer FAQ  
**Purpose:** Preempt the most predictable misunderstandings 

---

# 1. Is AIAL trying to decide whether AI-generated code is copyrightable?

**No.**

AIAL v2 should not claim to resolve that question.  
Instead, it should provide:

- a conservative permissive grant,
- provenance-aware declarations,
- and (optionally) a contributor-limited no-claim / covenant posture.

The goal is to reduce ambiguity, not to pretend unsettled law is settled.

---

# 2. Is AIAL saying “generated-origin” means public domain?

**No.**

A `generated-origin` declaration is a **provenance label**, not a conclusive legal determination.

At most, if explicitly paired with a no-claim declaration, it means:

- the declaring contributor does not assert rights to the extent they may exist, and/or
- the contributor grants fallback permissions to the broadest extent available.

That is intentionally narrower and safer than saying:
- “this file is public domain.”

---

# 3. Why not just use MIT?

A fair criticism.

The answer is: if the only goal were permissive licensing, MIT may be enough.

The distinct value AIAL is trying to explore is:

- explicit provenance disclosure,
- conservative handling of declared generated-origin contributions,
- and a structured way to say:
  - “to the extent I hold rights here, I choose not to assert them (or I grant broad fallback permissions).”

If that can’t be done without excessive complexity, that is itself useful feedback.

---

# 4. Is AIAL dependent on SPDX changes?

**No (for v2 direction).**

That was a weakness in the earlier iteration.

The revised approach should assume:
- AIAL works even if SPDX never adopts AI-specific tags.

Any SPDX-like examples should be:
- optional
- illustrative
- non-normative

---

# 5. Are file-level labels legally decisive?

**No.**

File-level labels may be:
- practical documentation
- useful reuse signals
- provenance representations

But they should not be treated as:
- conclusive proof of no human authorship
- conclusive proof of public domain status
- complete chain-of-title analysis

---

# 6. What about mixed authorship inside a file?

That is one of the hardest problems, and AIAL v2 should treat it conservatively.

If a file is:
- mixed
- partially segmented
- uncertain
- stale in metadata

Then the safe default is:

- do **not** infer no-claim
- do **not** infer absence of rights
- do **not** treat the file as “public domain by label”

This is why `mixed` and `unknown` should be first-class states.

---

# 7. What about inherited or vendored third-party code?

AIAL must not override upstream licensing.

Any `inherited` or similar provenance declaration should be read as:
- documentation only,
- preserving upstream terms,
- not altering separate obligations or rights.

---

# 8. Why remove AI-training-trigger language?

Because if OSI compatibility remains a serious goal, AI-training-specific conditions are likely to create avoidable problems:

- they may be read as use-triggered restrictions
- they may raise technology-neutrality concerns
- they may exceed conventional permissive license expectations

If provenance around AI training matters, it is safer to address it in:
- policy notes
- FAQs
- ethical requests
- non-binding guidance

---

# 9. Does the license text itself being AI-assisted matter?

Probably not in any meaningful way.

A license does not need to become a philosophical test case for its own authorship in order to be discussed on its merits.

That issue was a distraction in the earlier thread and should not be central going forward.

---

# 10. What is the question AIAL v2 is asking the community?

- “Is a narrower architecture — permissive grant + provenance declarations + optional contributor-limited no-claim — a coherent and useful direction worth refining?”
