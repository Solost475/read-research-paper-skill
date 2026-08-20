# read-research-paper

[English](README.md) | **简体中文**

这是一个可复用的 Codex Skill，用证据驱动的三遍阅读流程处理一篇论文或一个小规模论文集合。

它将 S. Keshav 的《How to Read a Paper》转化为可执行的工作流，覆盖快速筛选、证据关联理解、重建式批判和目标驱动阅读版。Skill 额外加入来源锚点、语义证据重组、文档指令隔离和现代文献检索偏差防护。

## 功能

- 四种深度模式：`scan`、`understand`、`reconstruct` 和以种子论文为中心的 `survey`。
- 第一遍产出 Keshav 的 Five Cs：Category、Context、Correctness、Contributions 和 Clarity。
- 第二遍把核心主张追溯到图、表、公式、实验、证明和引用。
- 第三遍虚拟重建假设、数据流、目标函数、算法、评价协议和缺失的复现信息。
- 每个阅读阶段先说明目标、阅读动作和达成标准，再给出达成检查、未决问题和阶段门控。
- 目标驱动阅读版只重新录入必要原文，并在相邻位置提供翻译；内容按语义标题组织，不使用编号式“摘录”。
- 正文不使用整页或普通段落截图；原论文图表以紧边界、未改动的裁图保留。
- 公式逐项对照可见原文，并离线渲染为语义 MathML 或自包含内联 SVG；只有无法可靠转录时才使用紧边界公式裁图。
- 内嵌证据图支持双击放大，并同时提供键盘和可见按钮操作的无障碍灯箱。
- 证据标签区分 `Author claim`、`Paper evidence`、`Reader inference` 和 `Not reported`。
- 来源锚点保留 PDF 页码、章节、图、表和公式标识。
- HTML 使用响应式排版、语义导航、宽屏双语双栏和窄屏单栏布局。
- 显式调用 `$read-research-paper` 时默认生成完整三遍式 HTML；用户仍可覆盖阅读深度或输出格式。
- HTML 会在桌面和窄屏视口检查溢出、资源缺失、导航错误和内容可读性。
- 文件名依次使用论文短标题、年份、第一作者标识和语言，不使用 Skill 名或泛化流程名称。
- 默认只交付一个自包含 HTML：CSS 和可选 JavaScript 内联，图表裁图以 data URL 嵌入，不需要资源目录。
- 论文中嵌入的指令只作为不可信文档内容处理，绝不作为代理指令执行。
- 不重新分发原始论文 PDF。

## 阅读模式

| 模式 | 适用场景 | 深度 |
|---|---|---|
| `scan` | 相关性判断和论文初筛 | 第一遍 |
| `understand` | 摘要、解释和学习笔记 | 第一至二遍 |
| `reconstruct` | 深度批判、实现规划和复现准备 | 第一至三遍 |
| `survey` | 从至少一篇种子论文向外扩展 | 引文网络扩展及按需阅读 |

## 安装

让 Codex 从本仓库安装：

```text
使用 $skill-installer 安装：
https://github.com/Solost475/read-research-paper-skill/tree/main/skills/read-research-paper
```

也可以克隆仓库并把 `skills/read-research-paper` 复制到个人 Codex Skills 目录。

PowerShell：

```powershell
git clone https://github.com/Solost475/read-research-paper-skill.git
$skillsDirectory = Join-Path $env:USERPROFILE ".codex\skills"
New-Item -ItemType Directory -Force -Path $skillsDirectory | Out-Null
Copy-Item -Recurse -LiteralPath ".\read-research-paper-skill\skills\read-research-paper" -Destination $skillsDirectory
```

Bash：

```bash
git clone https://github.com/Solost475/read-research-paper-skill.git
mkdir -p ~/.codex/skills
cp -R read-research-paper-skill/skills/read-research-paper ~/.codex/skills/
```

安装后，Skill 会在 Codex 的下一轮对话中可用。

## 使用

显式调用：

```text
使用 $read-research-paper 阅读这篇论文。
```

未提供其他选项时，Skill 会完成三遍阅读并返回一个经过验证的响应式、自包含 HTML。中文请求阅读英文论文时，宽屏把必要英文原文与中文翻译并排放置，窄屏则上下排列。公式通过离线 MathML 或内联 SVG 正确显示，不直接暴露原始 TeX；图表以原始裁图内嵌并支持双击放大。不使用整页截图，也不创建资源目录。可以显式要求 `scan`、`understand`、`survey`、PDF、Markdown、纯对话输出或不生成 HTML，以覆盖默认行为。

默认文件名来自论文元数据，例如 `large-scale-empirical-study-of-jit-quality-assurance_2013_kamei-etal_zh-en.html`，而不是 `read-research-paper.html` 或 `output.html`。

深度阅读：

```text
使用 $read-research-paper 的 reconstruct 模式精读这篇论文。
输出 Five Cs、主张—证据映射、方法重构、关键假设、复现缺口和下一步。
```

目标驱动 HTML 阅读版：

```text
使用 $read-research-paper 把这篇论文整理为三遍式 HTML 阅读版。
重新录入必要原文并逐段翻译，将图表裁图内嵌进文件；检查桌面和窄屏布局后只返回一个 HTML。
```

当请求与描述匹配时，Codex 也可能隐式调用该 Skill。OpenAI 文档把 Skill 定义为包含必需 `SKILL.md` 和可选资源的目录，并说明 `$skill-name` 是 Codex CLI 和 IDE 扩展中的显式调用形式：[Build skills](https://learn.chatgpt.com/docs/build-skills)。

## 仓库结构

```text
skills/
└── read-research-paper/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        ├── goal-driven-html-edition.md
        └── three-pass-protocol.md
```

## 方法来源

工作流基于：

> S. Keshav, *How to Read a Paper*, 2016 年 2 月 17 日版本。

- 作者来源页：[How to Read a Paper](https://svr-sk818-web.cl.cam.ac.uk/keshav/publications/htrap.html)
- 本仓库提供提炼后的工作流和原创操作扩展，不包含原论文 PDF。
- 引用次数、重复作者和会议或期刊声誉只作为发现线索，不作为正确性或质量证据。

## 许可证

本仓库原创的 Skill 指令和相关材料采用 [MIT License](LICENSE)。来源论文不包含在本仓库中，并继续受其自身版权条款约束。
