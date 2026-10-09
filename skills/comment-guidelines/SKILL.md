---
name: comment-guidelines
description: Apply maintainable code-comment and docstring conventions when creating, editing, or reviewing source code. Use for requests about comment quality, documentation inside code, or repositories that require standardized comments; do not use for user-facing prose documentation.
---

# Comment Guidelines

Write comments that preserve design knowledge the code cannot express clearly by itself.

## Choose The Comment Language

- Follow an explicit language requested by the user.
- Otherwise, follow an explicit repository policy for comment or docstring language.
- When neither specifies a language, write new or substantially rewritten comments and docstrings in Chinese.
- Before editing, briefly remind the user that Chinese is the default and English is available on request. Continue without waiting unless the user needs to choose.
- Do not translate existing comments solely to enforce the default language unless the user asks for translation or consistency work.

## Apply The Repository Convention

- Inspect nearby code before editing and match its docstring format, terminology, structure, and comment density.
- Prefer the repository's established convention over introducing a new documentation style.
- Keep comments and code synchronized in the same change; remove comments that are no longer true.

## Comment What Matters

Add comments or docstrings for:

- Public interfaces whose contracts, side effects, units, failure modes, or compatibility constraints are not clear from names and types alone.
- Intent, invariants, assumptions, units, boundary conditions, and data formats.
- Algorithm choices, correctness constraints, performance or memory tradeoffs, and security-sensitive behavior.
- Compatibility workarounds, version-specific behavior, external-system limitations, and deliberately unusual code.
- Failure modes where the reason for raising, retrying, falling back, or stopping is not evident.

Explain why the code is shaped this way and what must remain true. Let names, types, and straightforward control flow explain what the code does.

## Avoid Noise

- Do not narrate assignments, obvious branches, imports, or one-line operations.
- Do not duplicate type hints, function names, or implementation details in docstrings.
- Do not add comments to every line or section merely to satisfy a comment quota.
- Do not preserve dead code as comments; rely on version control.
- Do not add speculative TODOs. A TODO must state the concrete missing work and, when available, its issue reference or removal condition.

## Respect The Requested Mode

- When editing comments only, do not change runtime behavior, public interfaces, or unrelated formatting.
- When reviewing, report only actionable issues. Do not flag missing comments when the code is already self-explanatory.
- For each finding, identify the location, explain what knowledge is missing or stale, and suggest the smallest useful correction.
- Follow the user's explicit instructions when they differ from these general guidelines.

## Verify Before Finishing

- Review every changed comment against the final behavior, including error paths.
- Check that public interfaces and non-obvious constraints remain understandable without reading call-site history.
- Run the repository's relevant tests, formatter, or linter after comment-only edits when available.
- Preserve runtime behavior unless the user also requested a functional change.

