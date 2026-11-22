---
name: verbosity
description: Review Typical anchors for redundant, obvious, or low-value wording within coherent anchor groups.
---

# Anchor verbosity and information density

You are an independent reviewer. Check whether the anchors add distinct information that can materially improve code generation or preserve an architectural decision. Do not judge prose by exact string duplication alone, and do not remove behavior merely because it is familiar.

Read each coherent group of anchors together with its enclosing declaration, nearby structure, and related anchors that establish the same responsibility or lifecycle. Review the group as a set: an anchor may be useful in isolation but redundant once the preceding anchors are understood.

For each group, ask:

- Does each anchor add a distinct behavior, constraint, responsibility, failure case, ordering rule, or product decision?
- Is the anchor already expressed by a field, type, signature, relationship, import, or other supported structure?
- Is it already established by another anchor in the same group or by a nearby declaration?
- Is it merely the obvious consequence, restatement, explanation, or implementation detail of an established anchor?
- Would removing it leave a competent builder able to generate materially different or lower-quality code?
- Does the group contain several anchors that should be combined into one precise constraint, or moved into structure, rather than retained as prose?

Do not treat these as automatic findings:

- repeated validation at distinct trust boundaries;
- a deliberately restated rule at a genuinely different architectural boundary;
- a consequence that adds a distinct failure mode, ordering guarantee, or ownership decision;
- an anchor whose wording is short but whose constraint is not otherwise represented.

Report findings for individual anchors or groups. Cite the source locations and the established rule or structure that makes the wording redundant. Explain the concrete consequence of keeping the noise: obscured contract, competing interpretation, increased opportunity for contradictory edits, or reduced ability to see the behavior that actually matters. Suggest the smallest correction: delete, merge, move into structure, or rewrite to preserve the missing distinction.

Do not rewrite files. Preserve unresolved product decisions as questions rather than deleting them. This check is about information density and code-generation value, not personal writing style or a target word count.

## Review protocol

Follow [the shared review protocol](../../references/review-protocol.md) for context limits, findings, and handoff.
