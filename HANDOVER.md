# Handover — தொல்காப்பியப் பூங்கா Final Source Verification

This document is the canonical restart point for continuing the page-by-page source verification of **மு. கருணாநிதி — தொல்காப்பியப் பூங்கா** in a new chat or work session.

## 1. Repository and source

- GitHub repository: `pugazg/tolkappiyap-poonga`
- Canonical branch: `main`
- Source PDF filename: `TVA_BOK_0065569_தொல்காப்பியப்_பூங்கா.pdf`
- Source length: **537 PDF scan pages**
- Source used in the previous session: `/mnt/data/TVA_BOK_0065569_தொல்காப்பியப்_பூங்கா.pdf`

The `/mnt/data/...` path is session-specific. In a new chat, reattach the PDF or establish its new mounted path before doing any source comparison.

## 2. Current canonical Git state

At the time of this handover:

- `main` commit: `e9d04c2f9cb6311ef7572f874b0d434bfd24f4f6`
- Commit message: `Verify chapters 82 through 95 against source scans`
- Pull request merged: **PR #5**
- PR #5 changed files: **61**
- Chapters verified in that merge: **82–95**
- Scan range verified in that merge: **447–501**
- Text pages verified in that merge: **46**
- Existing illustration/photo pages retained: **9**

Before continuing, always search the latest commits on `main`. If `main` has advanced, treat the latest repository state as authoritative and reconcile this document before writing anything.

## 3. Overall verification progress

The repository currently records:

- Former `needs-review` text pages verified: **390**
- Remaining `needs-review` text pages: **32**
- Continuous chapter verification completed through:
  - **Chapter 95**
  - **Scan page 501**

The only remaining chapter batch is:

- **Chapters 96–100**
- **Scan pages 502–537**
- **32 text pages requiring direct source verification**
- **4 existing illustration/photo pages already marked `verified`**

After those 32 text pages are verified, the count should become:

- Former `needs-review` text pages verified: **422**
- Remaining `needs-review` text pages: **0**

## 4. Final batch boundaries

### Chapter 96 — ஐந்து பூதங்கள்

- Chapter path: `chapters/097-malar-96-ainthu-boothangal/README.md`
- Scan range: **502–504**
- Text pages: **502, 503, 504**
- Illustration pages: none
- Related நூற்பா: **91**

### Chapter 97 — உணர்ந்தோர் அறிவர்! அறிந்தோர் உணர்வர்!

- Chapter path: `chapters/098-malar-97-unarnthor-arivar-arinthor-unarvar/README.md`
- Scan range: **505–512**
- Text pages: **505–509, 511–512**
- Illustration page: **510**
- Related நூற்பா: **92**

### Chapter 98 — முதல் நூலும் வழி நூலும்!

- Chapter path: `chapters/099-malar-98-muthal-noolum-vazhi-noolum/README.md`
- Scan range: **513–518**
- Text pages: **513–518**
- Illustration pages: none
- Related நூற்பாக்கள்: **93, 95, 97, 98**

### Chapter 99 — குன்றத்து விளக்காகும்!

- Chapter path: `chapters/100-malar-99-kunrathu-vilakkaagum/README.md`
- Scan range: **519–523**
- Text pages: **519, 521–523**
- Illustration/photo page: **520**
- Related நூற்பா: **109**

### Chapter 100 — நூறாவது மலர்!

- Chapter path: `chapters/101-malar-100-nooraavathu-malar/README.md`
- Scan range: **524–537**
- Text pages: **524–525, 527–536**
- Illustration/photo pages: **526, 537**
- Related நூற்பா: **111**

### Exact remaining text-page set

```text
502 503 504
505 506 507 508 509 511 512
513 514 515 516 517 518
519 521 522 523
524 525 527 528 529 530 531 532 533 534 535 536
```

### Existing non-text pages that must remain untouched

```text
510 520 526 537
```

Do not rewrite illustration/photo pages merely to include them in the batch. Verify that their existing `page_type` and `status: "verified"` remain intact.

## 5. Source-render assets from the previous session

The previous session rendered the final range under paths similar to:

```text
/mnt/data/.../tolk_final_96_100/renders/page-502.jpg
...
/mnt/data/.../tolk_final_96_100/renders/page-537.jpg

/mnt/data/.../tolk_final_96_100/sheets/sheet-510-513.jpg
...
/mnt/data/.../tolk_final_96_100/sheets/sheet-534-537.jpg
```

These paths are not portable across chats and may no longer exist. In a new session, render scan pages 502–537 again from the PDF. A practical command is:

```bash
pdftoppm -f 502 -l 537 -jpeg -r 140 \
  TVA_BOK_0065569_தொல்காப்பியப்_பூங்கா.pdf \
  /mnt/data/tolk_final_96_100/renders/page
```

The exact output filenames produced by `pdftoppm` may require renaming or mapping. Confirm page numbers visually rather than assuming the filename mapping.

## 6. Non-negotiable verification rule

A text page may be changed to `verified` only after **direct visual comparison with the source scan**.

OCR may be used to locate likely differences, but OCR is not the authority. The printed scan is the authority.

Do not claim that a page was verified when only the existing Markdown, OCR output, a search snippet, or a prior commit was reviewed.

## 7. Required page-file transformation

For every verified text page, use this front matter pattern:

```yaml
---
scan_page: 502
printed_page: 501
section: "மலர் (96) — ஐந்து பூதங்கள்"
authority: "பொருளதிகாரம்"
iyal: "மரபியல்"
sutras: "91"
page_type: "text"
status: "verified"
transcription_method: "direct visual comparison with source scan"
---
```

At the end of the page:

- remove the temporary review note;
- add the source-page comment:

```html
<!-- மூல ஸ்கேன் பக்கம்: 502; அச்சுப் பக்கம்: 501 -->
```

Do not change the semantic metadata unless the scan or the chapter index proves it is wrong.

## 8. Text fidelity rules

Preserve the source exactly as printed, including:

- original Tamil spelling;
- sandhi and word joining;
- punctuation;
- quotation marks;
- நூற்பா wording;
- names and initials;
- dates;
- headings and subheadings;
- poetry lineation;
- lists of works in the final pages;
- source-specific forms that may look old-fashioned or inconsistent.

Do not silently modernise, standardise, translate, summarise, improve grammar, or replace a printed form with a form found on the internet.

When the source is genuinely unclear, do not guess. Leave the page as `needs-review` and document the uncertainty.

## 9. Chapter README update convention

For each of the five final chapter READMEs:

- change the text-page count status from `needs-review` to `verified`;
- retain the existing illustration/photo count;
- replace the status line with:

```text
நிலை: மூல ஸ்கேனுடன் இறுதி எழுத்து-ஒப்பீடு முடிந்தது
```

- change each text-page entry to `verified`;
- do not modify already verified illustration/photo entries;
- confirm the page totals match the chapter range.

Expected chapter counts after completion:

| Chapter | Total scans | Text pages | Illustration/photo pages |
|---|---:|---:|---:|
| 96 | 3 | 3 | 0 |
| 97 | 8 | 7 | 1 |
| 98 | 6 | 6 | 0 |
| 99 | 5 | 4 | 1 |
| 100 | 14 | 12 | 2 |
| **Total** | **36** | **32** | **4** |

## 10. Root README update after final verification

Update the final source-comparison section so it truthfully reports completion. The intended result is:

```text
- **மலர்கள் (2)–(100) — ஸ்கேன் 47–537**

- இறுதி ஒப்பீடு செய்யப்பட்ட `needs-review` உரைப் பக்கங்கள்: **422**
- மீதமுள்ள `needs-review` உரைப் பக்கங்கள்: **0**
```

Replace the “next review batch” line with a completion statement, for example:

```text
- 100 மலர்களின் அனைத்து `needs-review` உரைப் பக்கங்களுக்கும் மூல ஸ்கேனுடன் இறுதி எழுத்து-ஒப்பீடு முடிந்தது.
```

Do not claim that every front-matter page has been re-reviewed unless that work has actually been completed. The tracker should distinguish chapter-text completion from any separate future audit of front matter.

## 11. Git workflow for the final batch

1. Confirm the latest `main` commit.
2. Create a new branch from current `main`, for example:
   - `verify-chapters-96-100`
3. Assemble one atomic tree containing only:
   - 32 corrected text pages;
   - 5 chapter READMEs;
   - root `README.md`.
4. Expected changed-file count: **38**.
5. Commit message:

```text
Verify chapters 96 through 100 against source scans
```

6. Compare the branch against `main`.
7. Confirm:
   - branch is exactly one commit ahead;
   - no unrelated files changed;
   - all 38 expected files are present;
   - illustration/photo pages are absent from the changed-file list unless a genuine metadata defect was discovered.
8. Open a pull request.
9. Squash-merge into `main`.
10. Re-fetch and validate on `main`:
    - merged commit metadata;
    - root tracker;
    - first text page: scan 502;
    - a middle page from each chapter;
    - final text page: scan 536;
    - illustration page 537 remains verified and unchanged.

## 12. Known branch clutter

During the chapters 82–95 work, several temporary branches were created while recovering the atomic-tree workflow. They do not affect `main` and must not be treated as canonical:

```text
verify-chapters-82-95-checkpoint
verify-chapters-82-95-treebase
verify-chapters-82-95-staging
verify-chapters-82-95-atomic
verify-chapters-82-95-atomic2
verify-chapters-82-95-final
verify-chapters-82-95-z
```

The merged branch `verify-chapters-82-95` is also no longer the working source of truth. Always begin from `main`.

A debug file was created only on a temporary checkpoint branch during tool testing. It is not on `main` and must not be merged.

## 13. Useful completed commit history

```text
1b0e9b9b0124ba24f267bdd6300da18c122638ac  Verify chapters 7–11
1847d2ff1176a002f0b2d6e1c188e64612d5be27  Verify chapters 12–16
80ac154e278e9cbcbb57ef214d473c7c0bd88b07  Verify chapters 17–21
ad9ef46f6a0ffc8bbf2e3747fd5ca2d9143b51ad  Verify chapters 22–31
9a715a0f007671ede39496cea0d264587d39eff2  Verify chapters 32–41
06bbaa3db6e99d3bb7fa6e49728276e68b179b78  Verify chapters 42–51
fa34a0ed7ac3b974ea60ea9a3d6aec40be630850  Verify chapters 52–61
271c81b387109824c6c461d237c3e8aac1c95c7b  Verify chapters 62–71
3fbbb5af448b51a42cd746003f9dacac0cdd9f96  Verify chapters 72–81
e9d04c2f9cb6311ef7572f874b0d434bfd24f4f6  Verify chapters 82–95
```

## 14. Restart prompt for a new chat

Use the following prompt with the source PDF attached:

> Continue the final source-verification batch in `pugazg/tolkappiyap-poonga`. Read `HANDOVER.md` first and treat it as the canonical project state. Verify chapters 96–100, scan pages 502–537, directly against the attached PDF. Correct only the 32 text pages, retain the four verified illustration/photo pages, update the five chapter READMEs and root tracker, validate the expected 38-file atomic change set, and squash-merge it into `main`. Do not use OCR as the authority and do not modernise the printed text.

## 15. Completion criteria

The project’s current chapter-text verification phase is complete only when all of the following are true:

- chapters 96–100 have been visually compared page by page;
- all 32 remaining text pages are `verified`;
- all five final chapter READMEs are synchronized;
- root tracker reports **422 verified / 0 remaining**;
- the exact 38-file change set is validated;
- the pull request is squash-merged;
- the merged files are rechecked on `main`;
- no source wording has been silently corrected or modernised.
