# Paragraph layout flicker evidence

This branch contains evidence for a GenOffice Docs layout recovery fix, separate from the implementation PR.

## Reproduce

1. Download `01_layout_typography_english.docx` (English synthetic data; mixed portrait/landscape sections).
2. Open it in GenOffice and place the caret at the end of the first-page subtitle or metadata paragraph.
3. Press Enter. The original behavior temporarily shifts the paragraph left of the page text margin.
4. Wait for deferred pagination: its position recovers.

The two PNGs show the original Chinese document and the reported bug, not screenshots of the fixed result. The original Chinese DOCX is retained for traceability. In the English version, the first-page subtitle begins `01 Layout and Display` and the metadata begins `Synthetic test data`.

`before-pagination.json` and `after-pagination.json` record browser measurements from an isolated editor harness using the original document's opening blocks, actual editor extensions and document styles. The harness compares the original decoration mapping with the fix: the original shifts -164.4 CSS pixels immediately after Enter; the fix shifts 0. After authoritative pagination, both shift 0. This is not a full native eight-page rendering certification.

The original Chinese document SHA-256 is `7e5aefaccff966b6d8456bbdc5bf122242642d40b485ec9efee272f0f8e9f4ec`.

## English reproduction document

Only the document text and title metadata were translated. Section geometry, column settings, table structures, images and all other package parts are unchanged. The English document was rendered with bundled LibreOffice and all eight pages visually reviewed. The browser measurement JSON files above refer to the original Chinese document.

English DOCX SHA-256: `e799417cf3cf7d2622d86249026d6d0e83ae5aae3cfd9cf3a4edf7a52e2128c0`.
