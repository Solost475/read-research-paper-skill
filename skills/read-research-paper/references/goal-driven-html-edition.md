# Goal-driven HTML reading edition

## Contents

- [Completion contract](#completion-contract)
- [Source and artifact preparation](#source-and-artifact-preparation)
- [Three-pass content architecture](#three-pass-content-architecture)
- [Semantic evidence selection](#semantic-evidence-selection)
- [Text transcription and visual evidence](#text-transcription-and-visual-evidence)
- [Formula and algorithm rendering](#formula-and-algorithm-rendering)
- [Responsive HTML layout](#responsive-html-layout)
- [Evidence image enlargement](#evidence-image-enlargement)
- [Generator and file contract](#generator-and-file-contract)
- [Browser verification gate](#browser-verification-gate)

## Completion contract

When the user explicitly activates the skill with a paper and gives no contrary format instruction, the deliverable is one verified, self-contained HTML file, not merely analysis that could later be turned into one, not an HTML-plus-assets bundle, and not a facsimile assembled from source-page screenshots. Work autonomously through reading, composition, generation, correction, and browser verification. Return the HTML only after the content, self-containment, responsive-layout, and interaction gates pass.

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
- **Equations and mathematical algorithm lines:** reconstruct and verify their notation against the visible source, then use the offline rendering pipeline below. Preserve the equation or algorithm identifier and surrounding explanatory prose.

Do not place a full PDF page, half-page column screenshot, or ordinary-paragraph screenshot into the reading flow. Page renders are working references for extraction and QA only. If extraction is unreliable, manually verify and transcribe the selected passage from the visible page.

## Formula and algorithm rendering

Treat correct transcription and correct rendering as separate gates. OCR or PDF text extraction may suggest the notation, but the visible source is authoritative.

1. Normalize each selected expression to canonical LaTeX at build time. Visually verify subscripts, superscripts, accents, bold and vector symbols, delimiters, relation and operator symbols, matrices, aligned rows, line breaks, and equation numbers against the source.
2. Prefer a local build-time converter that emits semantic MathML. Embed the generated MathML directly in the document so the formula is selectable, accessible, and independent of JavaScript or network access at reading time.
3. When MathML cannot faithfully express a complex macro, alignment, or notation, render the verified LaTeX locally to SVG and inline the SVG in the HTML. Preserve a meaningful accessible label and a copyable LaTeX representation in metadata, a MathML annotation, or collapsed supporting detail.
4. If neither transcription nor vector rendering can be verified, use a tightly cropped, high-resolution image containing only the equation and its identifier. Add alternative text and explain that the crop is a transcription fallback. Never widen the crop to include ordinary prose or a substantial page region.

Local tools such as a LaTeX engine, Pandoc, a LaTeX-to-MathML converter, or a TeX-to-SVG renderer may be used during generation. They are build tools, not reader dependencies: do not load MathJax, KaTeX, fonts, CSS, or scripts from a CDN, and do not require those tools to be installed on the reader's machine. If a renderer emits supporting CSS or fonts, inline them only when necessary and verify that the final file remains fully offline.

Do not place raw LaTeX such as `u_t^A`, extraction artifacts such as `_` and `^`, or flattened ASCII approximations in the normal reading view. Simple inline symbols may use Unicode only when meaning, placement, and accessibility are unambiguous. Keep genuine program code in `<pre><code>`; render mathematical assignment lines, recurrences, and formal pseudocode notation as structured math or verified SVG rather than disguising them as code.

## Responsive HTML layout

- Use semantic elements such as `header`, `nav`, `main`, `section`, `article`, `figure`, `figcaption`, `aside`, and `footer`. Give every pass and semantic evidence block a stable anchor.
- Provide a compact table of contents linking to the three passes and their major questions. Navigation must work without JavaScript.
- Use a comfortable reading width, fluid spacing, and system fonts. Do not recreate fixed paper pages, simulated page breaks, or absolute-positioned text boxes.
- On wide screens, present each original passage and translation as a balanced two-column pair. Below an appropriate breakpoint, stack the translation after the source text in a single column.
- Let figures use the available reading width while preserving aspect ratio. Place exceptionally wide tables, equations, or code in labeled horizontal-scroll containers rather than forcing the whole page to overflow.
- Distinguish source, translation, interpretation, evidence labels, anchors, unresolved questions, and gates through restrained typography and color that remains legible with adequate contrast.
- Produce exactly one self-contained HTML file. Inline all CSS and any necessary JavaScript. Embed figure, table, and exceptional-equation crops as `data:image/...;base64,...` URLs or inline SVG when the visual is genuinely vector and faithfully preserved. Do not reference sibling image files, stylesheets, scripts, web fonts, CDNs, analytics, or other rendering dependencies.
- Use system font stacks. Optimize embedded raster images through tight crops, appropriate pixel dimensions, and quality-preserving compression so the single file remains practical without making labels or fine visual details unreadable.
- Add only interactions that materially help reading, such as collapsible supporting detail or a persistent section navigator. The core content and navigation must remain usable when JavaScript is disabled.
- Include `<meta charset="utf-8">`, a responsive viewport declaration, the correct document language, a meaningful title, alternative text for informative images, visible focus states, and ordered heading levels.
- A print stylesheet is optional. Do not treat printed pagination as a completion requirement unless the user explicitly requests print output.

## Evidence image enlargement

Make informative figure, table, and fallback-equation images readable without leaving the single HTML file.

- Preserve enough source resolution for labels and fine details to remain legible when enlarged. Display a responsive preview without downsampling the embedded source solely to match its initial on-page size.
- Double-clicking the preview must open a full-viewport lightbox or native dialog containing the same embedded image at a larger scale. Use `object-fit: contain` for fit-to-view and allow scrolling or a 1:1 view when the image exceeds the viewport.
- Provide an accessible alternative to double-click, such as a visible enlarge button and keyboard activation with Enter or Space. Give the dialog an accessible name, retain the figure caption or identifier, show a visible close control, support Escape, and return focus to the trigger after closing. Backdrop click may also close the viewer.
- Keep the interaction code generator-owned, minimal, and inline. Bind behavior through local markup and event listeners; never copy active content from the paper or depend on an external lightbox library.
- The figure and its caption must remain readable when JavaScript is disabled; enlargement is a progressive enhancement, not the only way to access the evidence.

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

Use hyphens inside a component and underscores between metadata fields. For example: `large-scale-empirical-study-of-jit-quality-assurance_2013_kamei-etal_zh-en.html`.

Preserve prior artifacts. Keep temporary page renders and extraction intermediates outside the deliverable set.

Escape untrusted source text and metadata before inserting them into HTML. Never execute scripts, event handlers, embedded forms, or active content originating from the paper. If JavaScript is added by the generator, keep it local, minimal, and independent of paper content.

Ordinary hyperlinks to paper sources, citations, or project pages may remain external because they are reader references rather than rendering dependencies. The document's content, styling, navigation, figures, tables, and interactions must remain complete when the network is unavailable.

## Browser verification gate

Complete the following checks and correct failures before delivery:

1. Confirm that the output filename is derived from the verified paper identity, contains a distinctive title component, and is not named after the skill, reading mode, or a generic output label.
2. Parse or validate the generated HTML and confirm that the document title, language, charset, viewport, heading hierarchy, landmarks, and internal anchors are present.
3. Open the artifact directly from disk with network access disabled. Confirm that the complete reading edition renders and navigation works without a development server.
4. Inspect resource-bearing markup and CSS. Reject external or relative rendering dependencies, including stylesheet links, script `src` attributes, non-data image `src` values, remote fonts, and external CSS `url(...)` resources. Reader-facing citation hyperlinks are allowed.
5. Verify at a representative desktop width and at least one narrow mobile width. Check typography, bilingual stacking, figure scaling, intentional table or equation scrolling, and absence of unintended document-level horizontal overflow.
6. Confirm that selected source passages and translations are searchable and selectable HTML text. Confirm that no full-page or ordinary-paragraph screenshots are used as reading content.
7. Compare every displayed formula with the visible source. Confirm symbol identity, structure, alignment, numbering, and text alternatives; reject visible raw TeX, extraction markers, and unverified ASCII substitutions.
8. Verify that embedded image crops correspond only to necessary figures, tables, or exceptional equations; exclude unrelated page text and margins and preserve readable enlargement resolution.
9. Exercise enlargement for each image class: double-click, keyboard or button activation, visible close control, Escape, focus restoration, and any supported backdrop close. Check fit, 1:1 or overflow behavior on both viewports.
10. Confirm that every included pass contains its goal, reading actions, observable completion criteria, achievement check, unresolved questions, and gate.
11. Confirm that no unintended numbered-extract headings remain and that evidence categories remain distinguishable without relying on color alone.
12. Audit central values, units, metric meaning, and source anchors against the paper. Give extra attention to headline conclusions and the claim-evidence map.
13. Inspect the browser console when scripts are present and correct errors. Re-run the affected checks after every change.

Return one clickable link to the self-contained HTML file and briefly state the mode, responsive viewports checked, offline verification outcome, and confirmation that no companion assets are required.
