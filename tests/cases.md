# Behavioral Test Cases

Run these cases in a clean conversation with the skill installed. Evaluate both whether the skill activates and whether the result follows the expected behavior.

## Direct activation

### Chinese default

Request:

```text
使用 $comment-guidelines 为这个状态机补充必要注释，不要改变代码行为。
```

Expected behavior:

- Reminds the user that Chinese is the default and English is available.
- Continues without waiting for a language choice.
- Adds only comments that explain state invariants, transition constraints, or other non-obvious intent.
- Does not change executable code.

### Explicit English

Request:

```text
Use $comment-guidelines to improve these docstrings. Write them in English.
```

Expected behavior:

- Uses English without asking whether Chinese is preferred.
- Preserves the repository's docstring format and terminology.
- Does not duplicate names, parameters, or type hints when they are already self-explanatory.

## Indirect activation

Request:

```text
这些注释已经和实现不一致了，请修正，并解释这个重试次数为什么不能随便增加。
```

Expected behavior:

- Applies the skill because the request concerns comment correctness and non-obvious constraints.
- Removes or corrects stale comments.
- Explains the retry constraint rather than narrating the retry loop.

## Repository language policy

Context:

```text
The repository's AGENTS.md requires all source comments to be written in English.
```

Request:

```text
使用 $comment-guidelines 完善这里的注释。
```

Expected behavior:

- Uses English because an explicit repository language policy takes precedence over the Chinese default.
- Still informs the user which language rule is being followed when useful.

## Review-only mode

Request:

```text
使用 $comment-guidelines 评审这个文件的注释质量，只报告问题，不修改文件。
```

Expected behavior:

- Does not edit files.
- Reports only actionable findings with locations and minimal corrections.
- Does not complain about missing comments when names, types, and control flow are self-explanatory.

## Should not activate

The skill should not be selected solely for these requests:

- Write a user-facing README for this project.
- Explain this function to a beginner without editing or reviewing source comments.
- Generate product documentation from an OpenAPI specification.

## Edge cases

- A trivial getter should not receive a comment that merely repeats its name.
- A bit mask with a protocol-defined layout should document the external format or constraint.
- A compatibility workaround should explain the affected version and removal condition when known.
- A TODO without concrete missing work should not be introduced.
- Existing comments should not be translated merely to force language uniformity.

## Provenance and lifecycle

Request:

```text
使用 $comment-guidelines 为这个受监管的结算阈值和临时兼容方案补充注释。
```

Expected behavior:

- Records the known regulation, requirement, benchmark, or upstream issue rather than inventing a source.
- Explains the threshold's unit and derivation when that information is available.
- Uses the appropriate marker instead of labeling every issue as TODO.
- Includes a tracking reference and removal condition for a temporary workaround when known.

## Module and algorithm documentation

Request:

```text
使用 $comment-guidelines 为这个一致性哈希模块和核心算法添加必要注释。
```

Expected behavior:

- Adds a module comment only when the module has a meaningful architectural responsibility.
- Describes the module boundary, important invariants, and relevant design references.
- Summarizes non-obvious algorithm stages and relevant complexity without narrating each line.

## Conditional references

- Cross-team ownership or deprecation work should load `references/advanced-cases.md`.
- Language-specific public API documentation should load only the relevant section of `references/language-conventions.md`.
- Ordinary comment edits should not load either reference unnecessarily.

