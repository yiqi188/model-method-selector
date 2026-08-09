# Model Method Selector

一个同时支持 Codex 和 Claude Code 的数学建模方法筛选 Skill。它会根据题目结构、数据特征和论文证据在内部比较候选方法，默认直接输出融合后的最优“建模思路/大纲”。

## 功能

- 根据题目结构建立可解释的基线模型
- 提取并核对论文中的模型、算法、实验条件与局限
- 在相同数据、目标、约束和指标下比较候选方法
- 区分数学模型与求解算法，避免用启发式算法替代可行的精确解
- 支持抽样质检、生产检测、拆解回流、多阶段装配和次品率不确定性决策
- 默认隐藏论文编号、证据评分和淘汰过程，直接交付可实现的建模思路/大纲

## Codex 版本

Codex 版本位于仓库根目录：

```text
SKILL.md
agents/openai.yaml
```

在仓库根目录执行以下 PowerShell 命令安装：

```powershell
$target = "$env:USERPROFILE\.codex\skills\model-method-selector"
New-Item -ItemType Directory -Force $target | Out-Null
Copy-Item .\SKILL.md $target
Copy-Item -Recurse -Force .\agents $target
```

在 Codex 中显式调用：

```text
$model-method-selector

请比较我上传的材料，推荐最适合的解题方法和数学模型。
```

## Claude Code 版本

Claude 版本位于：

```text
claude/model-method-selector/SKILL.md
```

安装为个人 Skill 后，可在所有项目中使用：

```powershell
$target = "$env:USERPROFILE\.claude\skills\model-method-selector"
New-Item -ItemType Directory -Force $target | Out-Null
Copy-Item .\claude\model-method-selector\SKILL.md $target
```

也可以安装为当前项目专用 Skill：

```powershell
$target = ".\.claude\skills\model-method-selector"
New-Item -ItemType Directory -Force $target | Out-Null
Copy-Item .\claude\model-method-selector\SKILL.md $target
```

在 Claude Code 中直接调用：

```text
/model-method-selector

请比较我上传的材料，推荐最适合的解题方法和数学模型。
```

Claude 也会在用户请求与 Skill 描述匹配时自动调用。

## 建议输入

至少提供题目说明和数据。需要比较优秀论文时，建议同时提供论文 PDF，尤其是模型建立、算法、实验结果和局限性部分。只有摘要时，Skill 会将其用于发现候选方法，不会把摘要中的“最优”表述直接当作可比证据。

## 文件结构

```text
model-method-selector/
├── SKILL.md                         # Codex 版本
├── agents/
│   └── openai.yaml                 # Codex 界面元数据
├── claude/
│   └── model-method-selector/
│       └── SKILL.md                # Claude Code 版本
└── README.md
```

Claude Code Skills 格式参考：[Anthropic 官方文档](https://code.claude.com/docs/en/skills)与 [Agent Skills 规范](https://agentskills.io/specification)。
