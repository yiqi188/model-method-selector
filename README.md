# Model Method Selector

一个用于比较多篇论文摘要、数据和实验条件，并筛选适合当前问题的解题方法与数学模型的 Codex Skill。

## 功能

- 提取论文中的问题、数据、变量、模型、算法和验证方式
- 区分数学模型与求解算法
- 对比候选方法的适用条件、优点、局限和数据需求
- 输出首选方案、备选方案、不推荐方案和证据缺口
- 对无法从摘要确认的内容明确标记，不编造细节

## 安装

将本仓库目录复制到 Codex Skill 目录：

```powershell
Copy-Item -Recurse . "$env:USERPROFILE\.codex\skills\model-method-selector"
```

或者直接复制其中的 `SKILL.md` 和 `agents/` 目录。

## 使用

在 Codex 中显式调用：

```text
$model-method-selector

请比较我上传的论文摘要和数据，推荐最适合当前问题的建模方法和数学模型。
```

建议同时提供题目说明、论文摘要或 PDF，以及数据文件（CSV/XLSX）。

## 文件结构

```text
model-method-selector/
├── SKILL.md
└── agents/
    └── openai.yaml
```
