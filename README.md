# comment-guidelines

一个面向 Codex 的代码注释与 docstring 规范 skill。它帮助 Codex 保留代码无法清楚表达的设计知识，同时避免逐行解释、自明注释和与实现脱节的文档。

## 主要行为

- 仅为非显而易见的意图、约束、不变量、边界条件、数据格式和权衡添加注释。
- 默认使用中文编写新增或大幅改写的注释和 docstring，并在修改前提醒用户可选择英文。
- 用户明确指定的语言优先，其次遵循仓库明确规定的语言；两者都未指定时才默认中文。
- 尊重仓库已有的 docstring 格式、术语、结构和注释密度。
- 为业务规则、架构决策、性能数据和上游缺陷保留可追溯依据。
- 区分 `TODO`、`FIXME`、`HACK`、`NOTE`、`WARNING` 与 `REVIEW`，并记录临时方案的移除条件。
- 对承担架构职责的模块和真正复杂的算法提供必要的边界、阶段与复杂度说明。
- 注释专项任务不修改运行行为、公共接口或无关格式。
- 评审时只报告可操作的问题，不因代码缺少无必要的注释而制造问题。

## 安装

### 使用 Codex skill-installer

将仓库发布到 GitHub 后，在 Codex 中发送：

```text
使用 $skill-installer 安装：
https://github.com/<owner>/comment-guidelines/tree/main/skills/comment-guidelines
```

把 `<owner>` 替换为 GitHub 用户名或组织名。安装完成后，在下一轮对话中即可使用。

### 手动安装

Windows PowerShell：

```powershell
git clone https://github.com/<owner>/comment-guidelines.git
Copy-Item -Recurse -Force `
  ".\comment-guidelines\skills\comment-guidelines" `
  "$env:USERPROFILE\.codex\skills\comment-guidelines"
```

macOS 或 Linux：

```bash
git clone https://github.com/<owner>/comment-guidelines.git
cp -R ./comment-guidelines/skills/comment-guidelines \
  ~/.codex/skills/comment-guidelines
```

## 使用

显式调用：

```text
使用 $comment-guidelines 检查这个模块中的注释和 docstring，不要改变运行行为。
```

选择英文：

```text
使用 $comment-guidelines 完善这些注释，本次请使用英文。
```

也可以在仓库的 `AGENTS.md` 中约定自动应用：

```markdown
# Global Coding Convention

- Apply the `comment-guidelines` skill when creating, editing, or reviewing source code.
```

## 仓库结构

```text
comment-guidelines/
├── plugin.json
├── skills/
│   └── comment-guidelines/
│       ├── SKILL.md
│       ├── agents/
│       │   └── openai.yaml
│       └── references/
│           ├── advanced-cases.md
│           └── language-conventions.md
└── tests/
    └── cases.md
```

根目录的 `plugin.json` 使用可移植 Agent Plugins 格式，为后续作为 Codex 插件或加入 marketplace 做准备。仅安装 skill 时，只需要 `skills/comment-guidelines/`。

## 验证

使用 Codex 内置的 `skill-creator` 校验器：

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-creator\scripts\quick_validate.py" `
  ".\skills\comment-guidelines"
```

然后按照 [`tests/cases.md`](tests/cases.md) 检查触发边界、语言选择和输出质量。结构校验通过并不等同于行为测试通过。

## 发布版本

本项目使用语义化版本号。本次新增可追溯依据、标记生命周期和按需语言参考，版本更新为 `v0.2.0`；当行为稳定并完成真实项目验证后，再发布 `v1.0.0`。

## 参考来源

- [OpenAI Docs：Build skills](https://developers.openai.com/plugins/build/skills)
- [代码注释规范：从“写什么”到“怎么写”的完整指南](https://kb.hugogu.cn/wiki/tech/guidance/comments)

## License

[MIT](LICENSE)

