# read-research-paper

A reusable Codex skill for reading one research paper, or a small paper set, with an evidence-grounded three-pass workflow.

It distills S. Keshav's *How to Read a Paper* into an operational workflow for rapid screening, evidence-linked understanding, reconstruction-level critique, and goal-driven reading editions. The skill adds explicit source anchors, semantic evidence reorganization, document-instruction isolation, and modern literature-search safeguards.

中文简介：这是一个面向 Codex 的论文阅读 Skill，支持快速筛选、证据级理解、复现式深读、目标驱动的论文语义重排，以及从种子论文扩展相关工作的流程。

## Features

- Four depth modes: `scan`, `understand`, `reconstruct`, and seed-centered `survey`.
- Pass 1 produces Keshav's five Cs: Category, Context, Correctness, Contributions, and Clarity.
- Pass 2 traces claims to figures, tables, equations, experiments, proofs, and citations.
- Pass 3 virtually reconstructs assumptions, data flow, objectives, algorithms, evaluation, and missing reproducibility details.
- Each included pass opens with its goal, reading actions, and completion criteria, then closes with an achievement check, unresolved questions, and a gate.
- Goal-driven reading editions organize selected evidence under semantic headings instead of numbered excerpts, while keeping source text, translation, and reader commentary distinct.
- Evidence labels distinguish `Author claim`, `Paper evidence`, `Reader inference`, and `Not reported`.
- Source anchors use PDF pages, sections, figures, tables, and equations.
- Designed reading artifacts are rendered for page-by-page checks of overflow, clipping, orphaned headings, blank pages, and stage boundaries.
- Instructions embedded in papers are treated as untrusted document content, never as agent instructions.
- The original PDF is not redistributed.

## Reading modes

| Mode | Use case | Depth |
|---|---|---|
| `scan` | Relevance check and paper triage | Pass 1 |
| `understand` | Summary, explanation, and study notes | Passes 1-2 |
| `reconstruct` | Deep critique, implementation planning, and reproduction preparation | Passes 1-3 |
| `survey` | Expand outward from at least one seed paper | Citation-network extension plus selected passes |

## Install

Ask Codex to install the skill from this repository:

```text
Use $skill-installer to install:
https://github.com/Solost475/read-research-paper-skill/tree/main/skills/read-research-paper
```

Or clone the repository and copy `skills/read-research-paper` into your personal Codex skills directory.

PowerShell:

```powershell
git clone https://github.com/Solost475/read-research-paper-skill.git
$skillsDirectory = Join-Path $env:USERPROFILE ".codex\skills"
New-Item -ItemType Directory -Force -Path $skillsDirectory | Out-Null
Copy-Item -Recurse -LiteralPath ".\read-research-paper-skill\skills\read-research-paper" -Destination $skillsDirectory
```

Bash:

```bash
git clone https://github.com/Solost475/read-research-paper-skill.git
mkdir -p ~/.codex/skills
cp -R read-research-paper-skill/skills/read-research-paper ~/.codex/skills/
```

The skill becomes available to Codex on the next turn after installation.

## Use

Explicit invocation:

```text
Use $read-research-paper in understand mode to read this PDF.
Produce the five Cs, a claim-evidence map, limitations, and source anchors.
```

Deep reading:

```text
使用 $read-research-paper 的 reconstruct 模式精读这篇论文。
输出 5C、主张-证据映射、方法重构、关键假设、复现缺口和下一步。
```

Goal-driven reading edition:

```text
使用 $read-research-paper 把这篇论文整理为三遍式阅读版。
每遍说明目标、阅读动作和达成标准，按语义重排必要原文证据，并给出达成检查、未决问题与门控。
```

Codex may also invoke the skill implicitly when a request matches its description. OpenAI's documentation describes a skill as a directory containing a required `SKILL.md` and optional resources, and documents `$skill-name` as the explicit invocation form in Codex CLI and the IDE extension: [Build skills](https://learn.chatgpt.com/docs/build-skills).

## Repository layout

```text
skills/
└── read-research-paper/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml
    └── references/
        └── three-pass-protocol.md
```

## Method provenance

The workflow is based on:

> S. Keshav, *How to Read a Paper*, version of February 17, 2016.

- Author's source page: [How to Read a Paper](https://svr-sk818-web.cl.cam.ac.uk/keshav/publications/htrap.html)
- This repository provides a distilled workflow and original operational extensions; it does not include the source PDF.
- Citation count, repeated authors, and venue prestige are treated only as discovery signals, not evidence of correctness or quality.

## License

The original skill instructions and repository materials are released under the [MIT License](LICENSE). The source paper is not included and remains subject to its own copyright.
