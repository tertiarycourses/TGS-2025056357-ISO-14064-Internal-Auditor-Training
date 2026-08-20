# Courseware QA Report — v3.0

Course: ISO 14064 Internal Auditor Training  
Course code: TGS-2025056357  
QA date: 20 August 2026

## A. Package completeness — PASS

- 138-slide editable PPTX and matched PDF.
- Learner Guide in Markdown, DOCX and 36-page PDF.
- Lesson Plan in DOCX and 8-page PDF.
- Ten self-contained `activities/` folders.
- Activity parity: 10 `README.md`, 10 same-basename `README.pdf`, 10 printable Activity Pack PDFs and 10 editable XLSX workbooks.
- Assessment package: WA paper/key and Case Study paper/key in DOCX and PDF.

## B. Curriculum and traceability — PASS

- Course code, TSC, four learning outcomes, K1–K8 and A1–A8 are aligned across the deck, Learner Guide, Lesson Plan, activities and assessments.
- Useful coverage from both supplied reference decks is preserved and expanded; see `SOURCE-COVERAGE-v3.0.md`.
- All ten activities use one connected HarbourLight Electronics / Lumina 400 case and declare scenario, questions, detailed procedure, required evidence and acceptance criteria.
- Learner Guide contains 10 detailed-procedure sections and 90 numbered learner actions.
- Lesson Plan totals 480 minutes per day and maps slide ranges, activities and assessment windows.

## C. Presentation and document QA — PASS

- PPTX structural check: 138 slides, six embedded images, valid OOXML package, zero `Step N` tokens and zero `lab/labs` tokens.
- The initial visual review found wrapped-title collisions and procedure-like numbered workflows. These were corrected and the deck was rebuilt and re-rendered.
- Final slide review found no clipping, unintended blank slides, collisions, unreadable text or inappropriate image crops.
- Original ImageGen visuals appear on the cover and four topic dividers; all generated images contain no generated labels, logos or watermarks.
- All 36 Learner Guide pages, eight Lesson Plan pages and 32 assessment pages were rendered and visually inspected.
- All learner-facing PDFs passed `pdfinfo` syntax checks; all DOCX/PPTX files passed ZIP/OOXML integrity checks.

## D. Activity workbook and PDF QA — PASS

- Every workbook opens in LibreOffice, has six visible purpose-specific sheets, frozen headers, controlled entry lists, print settings and no broken render.
- All 60 workbook-sheet renders and all 40 activity-PDF pages were inspected.
- Markdown/PDF content parity is 10/10; activity folders use `activity`, not `lab`.

## E. Assessment QA — PASS

- Preserved legacy structure: WA has 8 open-ended questions, 60 minutes, K1–K8; Case Study has 4 open-ended questions, 60 minutes, A1–A8.
- Preserved Case Study mapping pairs: A1/A8, A2/A7, A3/A4 and A5/A6.
- Candidate papers use cover page 1, trainee information/instructions/grading on page 2, and assessed content from page 3.
- Answer keys contain expected responses and grading guidance without candidate response blocks.
- The installed WSQ assessment verifier passed all four rendered documents.

## F. Drive and TMS publication QA — PASS

- Verified Drive root `1MwrypHNm6Tp-1SjpQVpjEUyglDvL6z0D` contains the expected course folders before publication.
- Dry-run previewed all archives/uploads before the guarded write. Superseded files were moved into folder-level archives; no unrelated Drive folders were changed.
- MD5 readback passed for all PPT/LG/LP/assessment files. Activities readback passed with 40 local files, 40 remote files, zero missing, zero extra and zero mismatches.
- Candidate WA and Case Study papers anonymously return OOXML files.
- Direct Drive permission deletion returned HTTP 204 for both answer keys; anonymous requests now return HTML access barriers, not document bytes. Archived legacy answer-key public links were also removed.
- Authenticated TMS dry-run resolved seven learner-facing fields: trainer PPT, learner PDF, Learner Guide PDF, Lesson Plan PDF, WA paper, Case Study paper and Activities folder.
- TMS update returned HTTP 200; post-write readback confirmed all seven URLs public and serving the intended current artifacts.
- An idempotent semantic before/after digest matched (`638c2081...ffe0e7`), proving unrelated course data was preserved after excluding publication URLs, assessment-link state and volatile IDs/timestamps.

## G. GitHub publication QA — PASS

- Verified the actual default branch is `master`; pre-replacement remote SHA was `6f6578ce455c4761b1b57aebd7c11c15d98d18ac`.
- Staged 52 public files only: 26 text and 26 binary artifacts.
- Forbidden-path scan returned no assessment, answer-key, reference, QA-render, build-tooling, archive or environment paths.
- Credential-signature scan returned no staged private keys, access tokens or environment assignments.
- Replaced the stale remote with force-with-lease against the verified SHA. Replacement commit `9c6da906ba51929674ab3b597671ad434f1d9d07` matched remote `master` on readback.
- Updated the repository description and topics for ISO 14064/WSQ courseware and enabled Discussions; GitHub Pages was intentionally not enabled for this content repository.

## Command substitutions

- User command `/assessemnt-gen` was treated as the installed `/assessment-gen` command.
- `/tms-push-qa` is not installed. Its required control is implemented as a TMS dry-run, secret-safe before snapshot, complete update and post-write URL readback.
- The Drive script does not implement `--help`; an initial probe reached its live archive phase before interruption. Immediate inventory showed no current top-level course file had changed. The release was then completed through the documented dry-run, guarded write, checksum readback and permission audit; the interrupted probe is not counted as a passed pre-write check.
