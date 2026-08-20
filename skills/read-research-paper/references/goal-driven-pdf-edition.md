# Goal-driven PDF reading edition

## Contents

- [Completion contract](#completion-contract)
- [Source and artifact preparation](#source-and-artifact-preparation)
- [Three-pass content architecture](#three-pass-content-architecture)
- [Semantic evidence selection](#semantic-evidence-selection)
- [Text transcription and visual evidence](#text-transcription-and-visual-evidence)
- [Language and visual layout](#language-and-visual-layout)
- [Generator and file contract](#generator-and-file-contract)
- [Build and verification gate](#build-and-verification-gate)

## Completion contract

For an explicit `$read-research-paper` invocation with a paper and no contrary format instruction, the deliverable is a verified re-typeset PDF, not merely analysis that could later be turned into one and not a facsimile assembled from source-page screenshots. Work autonomously through reading, composition, generation, correction, and verification. Return the PDF only after the build and visual gates pass.

The default depth is all three passes. A user-selected reading mode may reduce or extend the content, while an explicit text-only or no-file request disables PDF generation. Do not interpret a requested PDF as permission to redistribute the unchanged source paper; create a transformative reading artifact containing only the evidence needed for analysis.

## Source and artifact preparation

1. Identify the paper version and obtain the best available PDF. Record title, authors, year, venue when stated, source location, retrieval or generation time, and a source hash when local tooling permits.
2. Extract text and render the source pages for inspection. Establish the mapping among PDF page numbers, printed page numbers, sections, figures, tables, equations, appendices, and code or artifact references. Do not reuse full-page renders as body content in the final edition.
3. Inspect the complete source for multi-column reading-order errors, missing glyphs, footnotes, captions, equations, and extraction gaps. Use rendered pages as the authority when text extraction and visible content disagree.
4. If revising an existing reading edition, inspect its generator, layout, manifest, and rendered pages first. Preserve its visual language and stable interface unless a change is required for correctness or the user requests a redesign.
5. Keep the previous PDF and manifest unchanged. Choose a distinct output name for the new edition.

## Three-pass content architecture

Every included pass begins with three reader-facing elements:

1. **Pass goal** - the cognitive state the reader should reach.
2. **Reading actions** - the material inspected and how evidence or visuals should be used.
3. **After this pass you can** - observable outcomes the reader can verify.

Every included pass ends with an evidence-grounded achievement check, unresolved questions, and the selected stage gate. Populate these for the actual paper; never leave generic prompts or empty templates.

### Pass 1 - identity, importance, and continuation decision

Organize title and research question, background, central thesis, claimed contribution, headline results, the five Cs, reference signals, and the continuation decision. The reader should be able to explain what the paper is, why it may matter, what remains unchecked, and whether deeper reading is justified.

### Pass 2 - argument and supporting evidence

Organize data and labels, variables, method overview, evaluation protocol, result-by-result interpretation, figure and table reading, a claim-evidence map, limitations, and open questions. The reader should be able to explain how each central claim is supported and distinguish measured results from author interpretation and reader inference.

### Pass 3 - virtual reconstruction and hidden assumptions

Organize the end-to-end data flow, objectives and equations, algorithm or component logic, artifact or public-script differences, traceable key numbers, explicit and implicit assumptions, failure modes, and a concrete reproduction plan. State which details are missing and what they block. Static reconstruction is not an executed reproduction; never describe it as reproduced results unless the experiments were actually run and verified.

## Semantic evidence selection

- Treat source passages, figures, tables, equations, and code fragments as evidence selected for a reading objective, not as items to enumerate.
- Use semantic headings such as the research question, the role of a method component, or the evidence supporting a claim. Do not use `Excerpt 1`, `摘录 2`, or equivalent numbered-extract labels unless explicitly requested.
- Select, reorder, merge, and deduplicate evidence to create a coherent path through each pass. A source paragraph belongs in the earliest pass where it performs its main cognitive role; later passes should cross-reference its anchored location instead of repeating it.
- Preserve original wording when presenting source text. Keep original text, translation, interpretation, and external verification visually distinct.
- Attach printed page, section, figure, table, equation, appendix, or code anchors as available. Label `Author claim`, `Paper evidence`, `Reader inference`, `Not reported`, and `Externally verified` consistently.
- Preserve exact values, metric direction, units, conditions, splits, and uncertainty. Verify important numbers against both visible source pages and extracted text when practical.

## Text transcription and visual evidence

Use different treatments for prose and visual objects:

- **Prose, headings, captions, and short textual definitions:** accurately transcribe only the portions needed for the reading goal and typeset them as selectable text. Preserve paragraph wording and order within each selected passage. Add the translation in a separate adjacent block.
- **Figures and tables:** crop the original visual object from the source PDF and keep it unchanged. Include its number, caption, page or section anchor, and a nearby explanation of what it establishes.
- **Complex equations:** prefer typesetting when accuracy can be verified; otherwise use a tight source crop containing only the equation and its identifier, then transcribe the surrounding explanatory prose.

Do not place a full PDF page, a half-page column screenshot, or a screenshot of an ordinary paragraph into the final reading flow. Page renders are permitted only as working references for extraction and QA. If OCR or text extraction is unreliable, manually verify and transcribe the selected passage from the visible page instead of falling back to a page image.

## Language and visual layout

- Use the user's language for navigation, explanations, and stage guidance. When the paper language differs, default to a bilingual edition: typeset each selected original passage and its translation together, with the user's language as the primary reading path. Avoid redundant translation when source and user languages match.
- Use a readable parallel layout when the content supports it; do not force narrow columns on equations, wide tables, or complex figures. Allow full-width evidence blocks where clarity requires them.
- Use a cover and running headers that describe a goal-driven three-pass reading edition, not an excerpt collection. Make pass boundaries visually unambiguous.
- Preserve original paper figures and tables without redrawing or altering their data unless the user asks for a transformation. Use tight screenshot crops of those visual objects and add anchored interpretation nearby; exclude unrelated page text and margins from the crop.
- Preserve the visual baseline of an existing edition: palette, typography, column logic, spacing rhythm, and figure treatment. Change only what improves the new cognitive structure or fixes layout defects.

## Generator and file contract

Prefer a deterministic, rerunnable generator over manual page editing. Reuse an existing generator when available. Keep its established command-line and manifest interfaces backward compatible unless the user explicitly authorizes an interface change.

Use descriptive, collision-safe filenames. A suitable default is `<paper_stem>_three-pass_goal-driven_<language>_edition.pdf`; retain earlier editions as comparison and rollback artifacts.

If an existing generator already uses a manifest, update it consistently and verify its page count and mode. Do not introduce a new manifest solely for this workflow. Keep working crops, page renders, and build intermediates outside the final deliverable set unless the user asks for them.

## Build and verification gate

Complete all applicable checks and correct failures before delivery:

1. Run syntax or static checks for the generator and perform a clean, complete build.
2. Open the PDF programmatically and confirm it has pages. If the generator has a manifest, verify that its page count and mode match the final file.
3. Extract final PDF text and confirm that selected source passages are present as text, their translations are distinct, and every included pass contains its goal, reading actions, observable completion criteria, achievement check, unresolved questions, and gate.
4. Confirm that no full-page or ordinary-paragraph screenshots are used as reading content. Verify that image crops correspond only to necessary figures, tables, or exceptional equations and exclude unrelated page material.
5. Confirm that no unintended numbered-extract headings remain and that source text, translations, reader inferences, external verification, and not-reported information remain distinguishable.
6. Audit central values, units, metric meaning, and source anchors against the paper. Give extra attention to values used in the headline conclusions or claim-evidence map.
7. Render every final page and inspect it for text overflow, clipped tables or figures, unreadable images, orphaned headings, abnormal whitespace, blank pages, inconsistent headers, and broken pass boundaries.
8. Rebuild after any correction and repeat the affected programmatic and visual checks. Completion requires the final render, not an earlier preview, to pass.

Return a clickable link to the PDF and briefly state the mode, page count, and verification outcome.
