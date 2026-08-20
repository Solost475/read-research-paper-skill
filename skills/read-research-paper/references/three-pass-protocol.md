# Three-pass paper-reading protocol

## Contents

- [Provenance and scope](#provenance-and-scope)
- [Stage contract and semantic source reorganization](#stage-contract-and-semantic-source-reorganization)
- [Pass 1 - obtain the bird's-eye view](#pass-1---obtain-the-birds-eye-view)
- [Pass 2 - understand content and evidence](#pass-2---understand-content-and-evidence)
- [Pass 3 - virtually reimplement the work](#pass-3---virtually-reimplement-the-work)
- [Literature-survey extension](#literature-survey-extension)

## Provenance and scope

This protocol distills S. Keshav, *How to Read a Paper*, version of February 17, 2016. The source presents a three-pass method and a citation-network procedure for literature surveys. The evidence-labeling and modern-bias checks below are operational extensions for reliable agent use.

Official source page: https://svr-sk818-web.cl.cam.ac.uk/keshav/publications/htrap.html

## Stage contract and semantic source reorganization

For a reader-facing multi-pass result, make the depth transition explicit.

At the start of every included pass, state:

1. **Goal** - the level of understanding this pass should produce.
2. **Reading actions** - the source regions and evidence types to inspect, plus how deeply to inspect them.
3. **Completion criteria** - what the reader should be able to explain, reconstruct, or decide when the pass is complete.

Use selected source material to achieve those goals, not to produce an excerpt inventory. Give every selected passage, figure, table, equation, or code fragment a semantic heading that names the problem it resolves or the evidence it contributes. Avoid numbered labels such as `Excerpt 1` or `摘录 2` unless the user asks for them. Preserve the source wording when presenting original text, keep translations separate, and attach page, section, figure, table, or equation anchors.

Reorder and group evidence when that creates a more coherent reading path. Deduplicate repeated passages; if later passes need the same item, refer back to its anchored location unless a side-by-side comparison requires repetition. Do not let a translation, paraphrase, or reader note appear to be original paper text.

At the end of every included pass, record:

1. **Achievement check** - what is now understood, with anchors.
2. **Unresolved questions** - what remains uncertain or not reported.
3. **Gate** - `continue`, `stop-sufficient`, `stop-irrelevant`, `pause-for-background`, or the pass-specific low-quality outcome.

For a designed reading artifact, preserve the requested visual language and original figures or tables unless editing is requested. Render it in the target medium. For HTML, inspect desktop and narrow viewports for overflow, clipping, broken navigation, unreadable typography, missing resources, and unclear stage boundaries.

## Pass 1 - obtain the bird's-eye view

### Goal

Decide what the paper is, why it might matter, and whether deeper reading is justified.

### Actions

1. Read the title, abstract, and introduction carefully.
2. Read section and subsection headings without reading their bodies.
3. Glance at mathematical content to identify the theoretical foundation and expected technical depth.
4. Read the conclusion.
5. Scan the references and mark familiar, foundational, repeated, and potentially relevant unread works.

### Required output: the five Cs

| C | Question |
|---|---|
| Category | What kind of paper is this: measurement, theory, method, system, dataset, benchmark, survey, position, or another type? |
| Context | Which problem, theory, prior work, and research line does it belong to? |
| Correctness | Do the major assumptions appear plausible at this depth? What cannot yet be checked? |
| Contributions | What does the paper claim to add? Separate novelty claims from demonstrated results. |
| Clarity | Can the central problem, method, and result be recovered from the paper's high-level structure? |

### Completion criteria

Pass 1 is complete when the reader can answer the five Cs, recover the problem, high-level method, and headline result in a short explanation, identify what cannot yet be checked, and make a justified gate decision.

### Gate

- `continue`: relevant and understandable enough for the next pass.
- `stop-sufficient`: the five Cs answer the user's question.
- `stop-irrelevant`: outside scope or based on an evidently unsuitable premise.
- `pause-for-background`: important but prerequisites prevent a sound second pass.

The source estimates five to ten minutes for a human reader. Use this only as a signal that Pass 1 must stay shallow.

## Pass 2 - understand content and evidence

### Goal

Explain the paper's main thrust and supporting evidence without yet resolving every proof or implementation detail.

### Actions

1. Read all sections with care, temporarily skipping dense proofs, long derivations, and low-level implementation detail that block the main argument.
2. Record the problem definition, central thesis, method structure, and key claims.
3. Inspect every figure, diagram, and table. Check axes, scales, units, legends, captions, error bars or intervals, sample sizes, and whether visual evidence supports the text.
4. Trace each central claim to an experiment, theorem, analysis, or cited result.
5. Record unfamiliar terms, acronyms, unanswered questions, and claims that need author clarification.
6. Mark relevant unread references for prerequisites, competing methods, datasets, or evaluation conventions.
7. Write a short explanation that includes supporting evidence rather than only paraphrasing the abstract.

### Required output and completion criteria

Produce a problem-and-thesis explanation, a claim-evidence map, an evaluation reading, and a list of limitations and open questions. Pass 2 is complete when the reader can accurately explain the paper's main argument and evidence, distinguish direct results from author interpretation and reader inference, and state which details still require reconstruction or external background.

### Gate

- `continue`: the task requires critique, reconstruction, or reproduction-level detail.
- `stop-sufficient`: the paper can now be accurately explained at the requested depth.
- `pause-for-background`: resolve missing prerequisites, then repeat the affected portion of Pass 2.
- `stop-low-quality`: core claims remain unsupported or the presentation prevents reliable interpretation; state concrete reasons.

The source estimates up to an hour for an experienced human reader. Treat this as a relative depth marker.

## Pass 3 - virtually reimplement the work

### Goal

Reconstruct the work closely enough to expose innovations, hidden assumptions, missing details, and plausible failure modes.

### Reconstruction checklist

1. Restate the problem, inputs, outputs, constraints, and success criteria without copying the abstract.
2. Enumerate every explicit and implicit assumption. Challenge necessity, realism, and sensitivity.
3. Rebuild the method as equations, pseudocode, a component graph, or a data-flow description, whichever best fits the paper.
4. Recover data provenance, preprocessing, split logic, training or optimization objective, hyperparameters, stopping rules, and inference procedure.
5. Recover the evaluation protocol: baselines, controls, metrics, statistical treatment, compute, seeds, ablations, robustness tests, and artifact availability.
6. Attempt one key derivation, worked example, or result-trace. Compare the reconstruction with the paper and record discrepancies.
7. Identify unsupported leaps, missing citations, confounders, leakage risks, weak comparisons, and analytical or experimental failure modes.
8. Record improvements, alternative presentations, and future-work ideas separately from the authors' claims.

### Evidence labels

- `Author claim`: explicitly stated by the paper.
- `Paper evidence`: directly shown by a result, proof, table, figure, or appendix.
- `Reader inference`: a reasoned conclusion not explicitly stated.
- `Not reported`: necessary information that the source does not provide.
- `Externally verified`: information checked against a current primary source; include its citation.

### Completion gate

A third pass is complete only when the reader can reconstruct the paper's argument and method, identify its strongest evidence, state its assumptions and weaknesses, and explain which missing details prevent faithful reproduction. Do not claim reproducibility merely because the narrative is understandable.

The source says this pass can take many hours for beginners and more than one or two hours for experienced human readers. It is the deepest mode, not a fixed runtime requirement.

## Literature-survey extension

Use this only when the user asks to expand a seed paper into nearby work or build a reading list from it. Use a dedicated literature-search workflow for broad searches without a seed paper.

1. Search an academic index with well-chosen keywords for three to five recent or highly cited seed papers. Run Pass 1 on each, then inspect their related-work sections and look for a current survey.
2. Identify shared citations and repeated authors as leads. Obtain key papers and inspect those researchers' recent primary publications to find active topics and venues.
3. Inspect recent proceedings or journal issues from the relevant venues. Pass 1 the candidate set and Pass 2 the selected core papers.
4. Iterate when the selected papers repeatedly cite an important work that the set omits.

Apply modern safeguards:

- Prefer primary papers and official proceedings or repositories.
- Verify current bibliographic metadata and versions.
- Correct for citation age, field size, author-network, venue, language, and availability bias.
- Treat citation counts and venue labels as discovery heuristics, never as evidence of correctness or quality.
- State search dates, queries, databases, inclusion rules, and known coverage gaps.
