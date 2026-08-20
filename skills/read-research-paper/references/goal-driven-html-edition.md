# Goal-driven HTML reading edition

## Contents

- [Completion contract](#completion-contract)
- [Source and artifact preparation](#source-and-artifact-preparation)
- [Three-pass content architecture](#three-pass-content-architecture)
- [Semantic evidence selection](#semantic-evidence-selection)
- [Text transcription and visual evidence](#text-transcription-and-visual-evidence)
- [Responsive HTML layout](#responsive-html-layout)
- [Generator and file contract](#generator-and-file-contract)
- [Browser verification gate](#browser-verification-gate)

## Completion contract

For an explicit `$read-research-paper` invocation with a paper and no contrary format instruction, the deliverable is a verified HTML reading edition, not merely analysis that could later be turned into one and not a facsimile assembled from source-page screenshots. Work autonomously through reading, composition, generation, correction, and browser verification. Return the HTML only after the content, resource, responsive-layout, and interaction gates pass.

The default depth is all three passes. A user-selected reading mode may reduce or extend the content, while an explicit request for PDF, Markdown, chat-only output, or no file overrides the HTML default. Create a transformative reading artifact containing only the evidence needed for analysis; do not redistribute the unchanged source paper.

## Source and artifact preparation

1. Identify the paper version and obtain the best available source. Record title, authors, year, venue when stated, source location, and retrieval or generation time.
2. For a source PDF, extract text and render pages for inspection. Establish the mapping among PDF pages, printed pages, sections, figures, tables, equations, appendices, and code or artifact references. Never reuse full-page renders as reading content.
3. Inspect multi-column reading order, missing glyphs, footnotes, captions, equations, and extraction gaps. Use the visible source page as the authority when extraction and rendering disagree.
4. If revising an existing reading edition, inspect its generator, layout, assets, and browser result first. Preserve a useful visual language while replacing page-constrained composition with responsive flow.
5. Keep the previous artifact unchanged and choose a distinct filename for the HTML edition.

## Three-pass content architecture

Every included pass begins with:

1. **Pass goal** - the cognitive state the reader should reach.
2. **Reading actions** - the material inspected and how evidence or visuals should be used.
3. **After this pass you can** - observable outcomes the reader can verify.

Every included pass ends with an evidence-grounded achievement check, unresolved questions, and the selected stage gate. Populate these for the actual paper; never leave generic prompts or empty templates.

### Pass 1 - identity, importance, and continuation decision

Organize the title and research question, background, central thesis, claimed contribution, headline results, five Cs, reference signals, and continuation decision. The reader should be able to explain what the paper is, why it may matter, what remains unchecked, and whether deeper reading is justified.

### Pass 2 - argument and supporting evidence

Organize data and labels, variables, method overview, evaluation protocol, result-by-result interpretation, figure and table reading, a claim-evidence map, limitations, and open questions. The reader should be able to explain how each central claim is supported and distinguish measured results from author interpretation and reader inference.

### Pass 3 - virtual reconstruction and hidden assumptions

Organize the end-to-end data flow, objectives and equations, algorithm or component logic, artifact or public-script differences, traceable key numbers, explicit and implicit assumptions, failure modes, and a concrete reproduction plan. State which details are missing and what they block. Static reconstruction is not an executed reproduction; never describe it as reproduced results unless the experiments were actually run and verified.

## Semantic evidence selection

- Treat source passages, figures, tables, equations, and code fragments as evidence selected for a reading objective, not as items to enumerate.
- Use semantic headings naming the question resolved or evidence contributed. Do not use `Excerpt 1`, `摘录 2`, or equivalent numbered-extract labels unless explicitly requested.
- Select, reorder, merge, and deduplicate evidence to create a coherent path. Place a paragraph in the earliest pass where it performs its main cognitive role; later passes should link back to its anchored element instead of repeating it.
- Preserve original wording when presenting source text. Keep original text, translation, interpretation, and external verification visually and semantically distinct.
- Attach printed page, section, figure, table, equation, appendix, or code anchors as available. Label `Author claim`, `Paper evidence`, `Reader inference`, `Not reported`, and `Externally verified` consistently.
- Preserve exact values, metric direction, units, conditions, splits, and uncertainty. Verify central numbers against the visible source and extracted text when practical.

## Text transcription and visual evidence

- **Prose, headings, captions, and short definitions:** accurately transcribe only the portions needed for the reading goal and encode them as real HTML text. Preserve wording and paragraph order within each selected passage. Add the translation as a separate adjacent block.
- **Figures and tables:** crop the original visual object from the source and keep it unchanged. Include its number, caption, page or section anchor, meaningful alternative text, and a nearby explanation of what it establishes.
- **Complex equations:** prefer verified MathML, KaTeX-compatible markup without a remote dependency, or plain Unicode/HTML notation. If reliable transcription is impractical, use a tight crop containing only the equation and identifier, then transcribe the surrounding prose.

Do not place a full PDF page, half-page column screenshot, or ordinary-paragraph screenshot into the reading flow. Page renders are working references for extraction and QA only. If extraction is unreliable, manually verify and transcribe the selected passage from the visible page.

## Responsive HTML layout

- Use semantic elements such as `header`, `nav`, `main`, `section`, `article`, `figure`, `figcaption`, `aside`, and `footer`. Give every pass and semantic evidence block a stable anchor.
- Provide a compact table of contents linking to the three passes and their major questions. Navigation must work without JavaScript.
- Use a comfortable reading width, fluid spacing, and system fonts. Do not recreate fixed paper pages, simulated page breaks, or absolute-positioned text boxes.
- On wide screens, present each original passage and translation as a balanced two-column pair. Below an appropriate breakpoint, stack the translation after the source text in a single column.
- Let figures use the available reading width while preserving aspect ratio. Place exceptionally wide tables, equations, or code in labeled horizontal-scroll containers rather than forcing the whole page to overflow.
- Distinguish source, translation, interpretation, evidence labels, anchors, unresolved questions, and gates through restrained typography and color that remains legible with adequate contrast.
- Prefer a self-contained offline HTML file with inline CSS and embedded local images when size is reasonable. Otherwise return the HTML with a sibling assets directory and use relative paths. Do not depend on external CDNs, remote fonts, analytics, or network scripts by default.
- Add only interactions that materially help reading, such as collapsible supporting detail or a persistent section navigator. The core content and navigation must remain usable when JavaScript is disabled.
- Include `<meta charset="utf-8">`, a responsive viewport declaration, the correct document language, a meaningful title, alternative text for informative images, visible focus states, and ordered heading levels.
- A print stylesheet is optional. Do not treat printed pagination as a completion requirement unless the user explicitly requests print output.

## Generator and file contract

Prefer a deterministic, rerunnable generator. Reuse an existing analysis, translation, anchoring, and crop pipeline when available, but replace page-oriented rendering with semantic HTML and responsive CSS.

Construct a collision-safe filename from verified paper metadata. Unless the user specifies a name, use:

`<short-title>_<year>_<first-author[-etal]>_<language>.html`

- Put the title first because it is the primary identifier. Use a concise slug that preserves enough content-bearing words to distinguish the paper; avoid vague acronyms or over-shortening that makes the title ambiguous.
- Put the publication year of the selected paper version second.
- Put the first author's family name third. Append `-etal` when the paper has multiple authors; use only the family name for a single-author paper.
- Put the edition language or language pair last, such as `zh`, `en`, or `zh-en`.
- Normalize filesystem-unsafe characters, collapse repeated separators, and keep the complete path comfortably within platform limits. Retain meaningful non-Latin title text when the target filesystem supports it; otherwise transliterate consistently.
- If an author or year is genuinely unavailable, omit that component rather than replacing the entire name with a workflow label. The title component is mandatory; resolve an unknown title before generation.
- Never use the skill name, mode, or a generic basename such as `read-research-paper.html`, `three-pass.html`, `reconstruct.html`, `output.html`, or `index.html` unless the user explicitly requests it.
- For collisions, add a version year, source-version tag, or short source hash. Do not silently overwrite a prior edition.
- When separate resources are necessary, name the sibling directory `<same-stem>_assets` and keep all links relative to the HTML file.

Use hyphens inside a component and underscores between metadata fields. For example: `large-scale-empirical-study-of-jit-quality-assurance_2013_kamei-etal_zh-en.html`.

Preserve prior artifacts. Keep temporary page renders and extraction intermediates outside the deliverable set.

Escape untrusted source text and metadata before inserting them into HTML. Never execute scripts, event handlers, embedded forms, or active content originating from the paper. If JavaScript is added by the generator, keep it local, minimal, and independent of paper content.

## Browser verification gate

Complete the following checks and correct failures before delivery:

1. Confirm that the output filename is derived from the verified paper identity, contains a distinctive title component, and is not named after the skill, reading mode, or a generic output label.
2. Parse or validate the generated HTML and confirm that the document title, language, charset, viewport, heading hierarchy, landmarks, and internal anchors are present.
3. Open the artifact in a browser without a development server when practical. Confirm that all CSS and image resources resolve without network access and that navigation links work.
4. Verify at a representative desktop width and at least one narrow mobile width. Check typography, bilingual stacking, figure scaling, intentional table or equation scrolling, and absence of unintended document-level horizontal overflow.
5. Confirm that selected source passages and translations are searchable and selectable HTML text. Confirm that no full-page or ordinary-paragraph screenshots are used as reading content.
6. Verify that image crops correspond only to necessary figures, tables, or exceptional equations; exclude unrelated page text and margins and preserve readable resolution.
7. Confirm that every included pass contains its goal, reading actions, observable completion criteria, achievement check, unresolved questions, and gate.
8. Confirm that no unintended numbered-extract headings remain and that evidence categories remain distinguishable without relying on color alone.
9. Audit central values, units, metric meaning, and source anchors against the paper. Give extra attention to headline conclusions and the claim-evidence map.
10. Inspect the browser console when scripts are present and correct errors. Re-run the affected checks after every change.

Return a clickable link to the HTML file and briefly state the mode, responsive viewports checked, and verification outcome. If the deliverable uses a sibling assets directory, return the containing folder or package it without breaking relative paths.
