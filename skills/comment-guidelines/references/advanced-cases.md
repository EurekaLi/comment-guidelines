# Advanced Comment Cases

Use this guidance only when the code contains one of these situations.

## Make Comments Actionable

- Replace vague warnings such as "special handling" or "be careful" with the exact constraint, risk, affected scope, and triggering condition.
- Link to a stable source when the explanation depends on information outside the repository. Do not include secrets, expiring credentials, or inaccessible personal links.

## Cross-Team Ownership

When another team or service owns the state or contract, document:

- who owns it;
- which direct mutations are forbidden;
- the supported API, client, or event path;
- any required review or coordination before changing the behavior.

Use ownership tags only when the repository defines them.

## Deprecation And Migration

For a deprecated public interface, state the replacement, the version where deprecation began, and the planned removal version or condition when known. Avoid promises about dates or versions that are not established.

## Complex Regular Expressions

For a regular expression whose intent is not evident from its name and tests, explain the input language, important groups or boundaries, and one or two representative matching or non-matching examples. Prefer decomposing or naming the expression when that makes the code clearer than a comment.

## Standard Tags

Tags such as `[PERF]`, `[SEC]`, `[COMPAT]`, `[REG]`, or `[ARCH]` can make constraints searchable, but use them only when the repository or team already defines their meaning. Do not introduce a private tag vocabulary in one file.

## Long Comments

Use paragraphs and short lists when a comment describes several cases or ordered stages. Keep the comment adjacent to the smallest code unit governed by it, and move durable design material to an architecture or decision document when it outgrows the code.

