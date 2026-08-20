# read-research-paper

**English** | [简体中文](README.zh-CN.md)

A portable Agent Skill for reading one research paper, or a small paper set, with an evidence-grounded three-pass workflow.

It distills S. Keshav's *How to Read a Paper* into an operational workflow for rapid screening, evidence-linked understanding, reconstruction-level critique, and goal-driven reading editions. The skill adds explicit source anchors, semantic evidence reorganization, document-instruction isolation, and modern literature-search safeguards.

## Features

- Four depth modes: `scan`, `understand`, `reconstruct`, and seed-centered `survey`.
- Pass 1 produces Keshav's five Cs: Category, Context, Correctness, Contributions, and Clarity.
- Pass 2 traces claims to figures, tables, equations, experiments, proofs, and citations.
- Pass 3 virtually reconstructs assumptions, data flow, objectives, algorithms, evaluation, and missing reproducibility details.
- Each included pass opens with its goal, reading actions, and completion criteria, then closes with an achievement check, unresolved questions, and a gate.
- Goal-driven reading editions re-typeset only the necessary source passages as selectable text with adjacent translation, organized under semantic headings instead of numbered excerpts.
- Full source-page and paragraph screenshots are excluded from the reading body; original figures and tables are retained as tight, unmodified crops.
- Formulas are verified against the visible source and rendered offline as semantic MathML or self-contained inline SVG, with a tightly scoped equation crop reserved for unresolvable cases.
- Embedded evidence images support double-click enlargement in an accessible inline lightbox, while preserving keyboard and visible-button controls.
- Evidence labels distinguish `Author claim`, `Paper evidence`, `Reader inference`, and `Not reported`.
- Source anchors use PDF pages, sections, figures, tables, and equations.
- HTML reading artifacts use responsive typography, semantic navigation, wide-screen bilingual columns, and narrow-screen single-column flow.
- Explicit activation defaults to a complete three-pass HTML reading edition; depth and output format remain user-overridable.
- HTML editions are checked in desktop and narrow viewports for overflow, missing resources, broken navigation, and content readability.
- Output filenames place a concise paper title first, followed by year, first-author label, and language; the skill name and generic workflow labels are not used as basenames.
- The default deliverable is one self-contained HTML file: CSS and optional JavaScript are inline, while figure and table crops are embedded as data URLs; no companion assets directory is required.
- Instructions embedded in papers are treated as untrusted document content, never as agent instructions.
- The original PDF is not redistributed.

## Reading modes

| Mode | Use case | Depth |
|---|---|---|
| `scan` | Relevance check and paper triage | Pass 1 |
| `understand` | Summary, explanation, and study notes | Passes 1-2 |
| `reconstruct` | Deep critique, implementation planning, and reproduction preparation | Passes 1-3 |
| `survey` | Expand outward from at least one seed paper | Citation-network extension plus selected passes |

## Portability

The core package follows the [Agent Skills specification](https://agentskills.io/specification): a `SKILL.md` entrypoint with standard frontmatter and relative links to supporting references. Its instructions are capability-based and contain no required vendor command, product path, model provider, shell, or named tool.

The `agents/openai.yaml` file is optional interface metadata for hosts that understand it. It is not part of the normative workflow; other hosts may ignore or remove it without changing the skill's behavior.

The complete HTML workflow requires the host to provide equivalent capabilities for reading the paper, writing a local file, inspecting PDF pages or webpages, cropping images, rendering mathematics offline, and checking the result in a browser. If a capability is unavailable, the agent must report that limitation rather than claim an unperformed verification.

## Install

Clone the repository, then copy the complete `skills/read-research-paper` directory into the skill location configured by your agent host:

```bash
git clone https://github.com/Solost475/read-research-paper-skill.git
```

Keep `SKILL.md` and `references/` together so relative links continue to work. After copying, refresh or restart the host if its skill discovery requires it. If the host does not implement directory-based skill discovery, load `SKILL.md` as the reusable instruction entrypoint and make the linked reference files available at their relative paths.

## Use

Platform-neutral activation example:

```text
Activate the read-research-paper skill and read this paper.
```

With no further options, this runs all three passes and returns one verified, self-contained HTML reading edition. For a Chinese-language request on an English paper, it re-typesets the necessary English paragraphs and places Chinese translations beside them on wide screens and below them on narrow screens. Formulas are rendered offline instead of exposing raw TeX, and faithful embedded figure and table crops can be enlarged by double-click. Full-page screenshots and companion assets directories are not used. Ask for `scan`, `understand`, `survey`, PDF, Markdown, chat-only output, or no HTML to override the default depth or artifact.

The default filename is derived from paper metadata, for example `large-scale-empirical-study-of-jit-quality-assurance_2013_kamei-etal_zh-en.html`, rather than `read-research-paper.html` or `output.html`.

Deep reading:

```text
Activate read-research-paper in reconstruct mode to study this paper.
Include the five Cs, claim-evidence map, method reconstruction, assumptions, reproducibility gaps, and next action.
```

Goal-driven HTML reading edition:

```text
Activate read-research-paper and turn this paper into a three-pass HTML reading edition.
Re-typeset the necessary source passages with translation, embed original figure and table crops, and return one self-contained HTML file after desktop and narrow-screen checks.
```

A host may also activate the skill automatically when a request matches its description. Selection syntax and discovery locations are host concerns, not part of this skill's behavior contract.

## Repository layout

```text
skills/
└── read-research-paper/
    ├── SKILL.md
    ├── agents/
    │   └── openai.yaml                # optional host UI adapter
    └── references/
        ├── goal-driven-html-edition.md
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
