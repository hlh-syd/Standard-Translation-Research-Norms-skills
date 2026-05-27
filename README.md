# 科研技能说明

`scientific-research` 是一个面向科研代码项目的 Codex skill，用来统一研究目录结构、分析脚本放置规则、结果输出规则、进展展示页面，以及对话结束后的备份记录。

这个 skill 的目标不是替代具体科研分析，而是为分析过程提供一套稳定的工程约束，让多轮对话下的项目空间保持一致、可追踪、可汇报。

## 适用场景

当你希望 Codex 在科研项目里遵循固定工作流时，可以使用这个 skill，例如：

- 初始化或整理科研项目目录
- 新建或归档分析脚本
- 维护 `plan`、`review`、`todolist`、`progress`
- 为科研项目生成面向非专业人员的讲解前端
- 在每次任务结束后按固定 JSON 格式写入 `backUp`

显式调用示例：

```text
Use $scientific-research to organize this research workspace, enforce the folder conventions, and update backup/progress artifacts.
```

## 核心约束

skill 会把以下目录视为项目根目录下必须存在的同级目录：

- `backUp`
- `ansisly`
- `results`
- `else`

其中 `ansisly` 的拼写会被原样保留，不会自动更正。

在 `ansisly/<项目名>` 下，要求存在以下一级目录：

- `script`
- `data`
- `plan`
- `review`
- `todolist`
- `progress`

这套规则的重点包括：

- 分析脚本不能直接堆在 `ansisly` 第一级目录下
- 方法分支和脚本变体要按约定分文件夹管理
- `plan/headplan.txt` 负责记录项目目标与整体研究框架
- `results` 必须与 `ansisly` 下的项目同名对应，并按 `results_MMDDHH` 分批输出
- `progress/progress.html` 和 `progress/项目讲解` 缺失时需要创建
- 对话结束后必须更新 `backUp`

## 目录中的文件

- [SKILL.md](C:/Users/he/Documents/Codex/2026-05-23/codex-exe/scientific-research/SKILL.md)
  定义 skill 的触发条件和执行流程。

- [references/workspace-rules.md](C:/Users/he/Documents/Codex/2026-05-23/codex-exe/scientific-research/references/workspace-rules.md)
  详细规定 `ansisly`、`results`、`else`、`data`、`plan`、`review`、`todolist`、`progress` 的目录与命名规则。

- [references/frontend-prompts.md](C:/Users/he/Documents/Codex/2026-05-23/codex-exe/scientific-research/references/frontend-prompts.md)
  存放两个可直接复用的长提示词：
  `项目讲解` 前端项目提示词和 `progress.html` 提示词。

- [references/backup-format.md](C:/Users/he/Documents/Codex/2026-05-23/codex-exe/scientific-research/references/backup-format.md)
  规定 `backUp` 的文件查找方式、分卷规则和 JSON 记录格式。

- [agents/openai.yaml](C:/Users/he/Documents/Codex/2026-05-23/codex-exe/scientific-research/agents/openai.yaml)
  提供 UI 显示名、简短描述和默认调用提示。

## 执行流程概览

使用这个 skill 时，Codex 应按下面顺序工作：

1. 确认项目根目录，并检查 `backUp / ansisly / results / else` 是否齐全
2. 选择或创建 `ansisly/<项目名>`
3. 补齐该项目下的 `script / data / plan / review / todolist / progress`
4. 按规则放置脚本、数据、结果和一次性文件
5. 需要前端讲解页面时，复用 `frontend-prompts.md` 中的模板
6. 工作完成后，再更新 `backUp`

## 设计取舍

这个 skill 把“给模型看的流程说明”和“详细规范文本”拆开了：

- `SKILL.md` 保持简洁，负责触发和主流程
- 详细规则放在 `references/`，避免每次触发都加载过多上下文

这样能减少上下文开销，同时保留你定义的严格规范。

