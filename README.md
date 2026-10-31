# Paragraph layout flicker evidence

This branch contains evidence for a GenOffice Docs layout recovery fix, separate from the implementation PR.

## Reproduce

1. Download `01_layout_typography.docx` (synthetic data; mixed portrait/landscape sections).
2. Open it in GenOffice and place the caret at the end of the first-page subtitle or metadata paragraph.
3. Press Enter. The original behavior temporarily shifts the paragraph left of the page text margin.
4. Wait for deferred pagination: its position recovers.

The two PNGs are original screenshots of the reported bug, not screenshots of the fixed result.

`before-pagination.json` and `after-pagination.json` record browser measurements from an isolated editor harness using the original document's opening blocks, actual editor extensions and document styles. The harness compares the original decoration mapping with the fix: the original shifts -164.4 CSS pixels immediately after Enter; the fix shifts 0. After authoritative pagination, both shift 0. This is not a full native eight-page rendering certification.

The document SHA-256 is `7e5aefaccff966b6d8456bbdc5bf122242642d40b485ec9efee272f0f8e9f4ec`.
