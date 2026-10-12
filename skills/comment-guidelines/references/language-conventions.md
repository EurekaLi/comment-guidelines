# Language-Specific Documentation Conventions

Repository rules take precedence. Use only the sections relevant to the current language, and include each field only when it adds contract information that names, types, and generated documentation do not already provide.

## Java And Kotlin

- Follow the repository's Javadoc or KDoc format for public APIs and framework extension points.
- Document preconditions, meaningful parameters and return semantics, declared or important runtime failures, concurrency guarantees, performance boundaries, and related alternatives when relevant.
- Use `@since`, `@see`, links, and deprecation metadata when they help callers migrate or understand compatibility.

## Python

- Follow the repository's established docstring convention, such as Google or NumPy style.
- Describe preconditions, units, return semantics, raised exceptions, side effects, thread or async safety, and examples only when they are not evident from the signature and types.
- Do not duplicate annotations or enumerate implementation steps that callers do not need.

## JavaScript And TypeScript

- Use JSDoc or TypeDoc conventions when the repository generates documentation or relies on editor hints.
- Add `@param`, `@returns`, `@throws`, `@example`, or `@deprecated` only when they communicate useful behavior beyond TypeScript types.
- For type assertions or framework-specific behavior, explain the contract or lifecycle guarantee that makes the unusual code safe.

## Go

- Follow Go documentation conventions for packages and exported identifiers.
- State whether a type's zero value is usable, whether it is safe for concurrent use, and which constructor or lifecycle callers must follow when those facts are non-obvious.
- Document meaningful error conditions and package-level invariants without restating the declaration.

## Verification Tools

Use the repository's configured tooling when available, such as docstring linters, Javadoc doclint, TypeDoc or ESLint documentation rules, Go documentation checks, and TODO/FIXME scanners. Do not introduce a new mandatory tool solely for a comment-only change.

