# Guidelines for Transcribing Kalaignar’s Works into Page-by-Page Markdown on GitHub

This document defines a reusable workflow for digitising books, speeches, letters, memoirs, articles, plays, poetry, and other works by **மு. கருணாநிதி (கலைஞர்)** as faithful, page-level Markdown repositories.

The core principle is simple:

> **The scan is the authority. Markdown is a faithful preservation layer, not a rewritten edition.**

## 1. Scope

Use these guidelines when a scanned book or PDF must be:

- read page by page;
- written into Markdown files;
- preserved in original page order;
- organised by volume, chapter, letter, speech, poem, or section;
- tracked and reviewed in GitHub;
- continued across many chats, agents, or work sessions.

These rules are suitable for:

- Murasoli letters;
- collected letters and correspondence;
- speeches and conference addresses;
- essays and political writing;
- memoirs and autobiography;
- novels and short stories;
- plays and screenplays;
- poems and song texts;
- grammar and literary commentary;
- multi-volume collected works.

## 2. Preservation principles

### 2.1 Source-first fidelity

Transcribe what the printed source contains, not what the transcriber thinks it should contain.

Preserve:

- wording;
- spelling;
- punctuation;
- capitalisation where relevant;
- Tamil sandhi and word joining;
- paragraph order;
- verse line breaks;
- headings and subheadings;
- letter numbers and dates;
- footnotes;
- signatures;
- captions;
- printed-page numbers;
- visible editorial marks that carry meaning.

### 2.2 No silent correction

Do not silently:

- modernise spelling;
- fix grammar;
- change political or historical terminology;
- expand initials;
- standardise names;
- replace a source quotation with an internet version;
- correct a நூற்பா, poem, or quotation from memory;
- merge repeated lines;
- remove apparent printing errors.

When a printed form appears doubtful, preserve it and record the doubt separately.

### 2.3 No invention

Never guess a missing or unclear word merely to make a sentence read smoothly.

If the scan is unreadable:

- retain `needs-review` status;
- mark the uncertain location explicitly;
- inspect a higher-resolution render;
- compare another edition only as supporting evidence, never as a silent replacement for the scan.

### 2.4 OCR is only an assistant

OCR may help locate text, but it must never be treated as the source of truth.

Common Tamil OCR failures include:

- `ழ / ள / ல` confusion;
- `ற / ர` confusion;
- missing pulli marks;
- broken ligatures;
- mixed Latin characters;
- page-number fragments inserted into body text;
- line-order errors in multi-column layouts;
- punctuation loss;
- incorrect word segmentation;
- omitted verse lines.

Every page marked `verified` must have been visually compared with the scan.

## 3. Repository strategy

### 3.1 One repository or one collection root

Choose a repository structure before transcription begins.

For a single book:

```text
README.md
HANDOVER.md
TRANSCRIPTION_RULES.md
metadata/
indexes/
pages/
chapters/
```

For a multi-volume collection:

```text
README.md
HANDOVER.md
KALAIGNAR_WORKS_MARKDOWN_GUIDELINES.md
volumes/
  volume-01/
    README.md
    metadata/
    indexes/
    pages/
    chapters/
  volume-02/
    README.md
    metadata/
    indexes/
    pages/
    chapters/
```

Each volume must be self-contained. Never mix pages from two source volumes in one page directory without an explicit volume prefix.

### 3.2 Separate source identity

Record for every source:

- exact source filename;
- work title;
- author;
- volume number;
- edition;
- publisher;
- publication year;
- total PDF scan pages;
- printed-page range;
- source URL or archive identifier when available;
- file hash, preferably SHA-256;
- date imported;
- known missing, duplicate, rotated, or damaged pages.

Recommended file:

```text
metadata/source.md
```

Recommended machine-readable companion:

```text
metadata/source.json
```

## 4. Page-level file design

### 4.1 One Markdown file per scan page

Every scan page must have a corresponding record, including:

- covers;
- title pages;
- copyright pages;
- contents pages;
- blank pages;
- text pages;
- illustration pages;
- photographs;
- advertisements;
- end matter.

Do not omit a page because it has no continuous body text.

### 4.2 Stable zero-padded names

Use scan-page order in filenames:

```text
pages/0001-cover.md
pages/0002-title-page.md
pages/0024-letter-3764-01.md
pages/0025-letter-3764-02.md
```

For multi-volume repositories, the volume directory supplies the volume identity:

```text
volumes/volume-49/pages/0024-letter-3764-01.md
```

Avoid renaming files after links and manifests have been created.

### 4.3 Recommended YAML front matter

Text page:

```yaml
---
scan_page: 24
printed_page: 23
volume: 49
section: "கடிதம் 3764 — சாதனைப் பட்டியலில் விட்டுப் போனவை!"
page_type: "text"
status: "needs-review"
source_filename: "TVA_BOK_0065839_கலைஞரின்_கடிதங்கள்_தொகுதி_49.pdf"
---
```

Verified text page:

```yaml
---
scan_page: 24
printed_page: 23
volume: 49
section: "கடிதம் 3764 — சாதனைப் பட்டியலில் விட்டுப் போனவை!"
page_type: "text"
status: "verified"
transcription_method: "direct visual comparison with source scan"
source_filename: "TVA_BOK_0065839_கலைஞரின்_கடிதங்கள்_தொகுதி_49.pdf"
---
```

Illustration/photo page:

```yaml
---
scan_page: 25
printed_page: 24
volume: 49
section: "கடிதம் 3764"
page_type: "illustration"
status: "verified"
---
```

Useful optional fields:

```yaml
letter_number: 3764
letter_date: "1989-01-01"
chapter_number: 12
chapter_title: "..."
authority: "பொருளதிகாரம்"
iyal: "மரபியல்"
sutras: "91"
language: "ta"
notes: "..."
```

Use only fields relevant to the work. Keep field names consistent across the repository.

## 5. Page types

Recommended controlled values:

```text
cover
title-page
copyright
publisher-note
foreword
contents
index
text
poetry
letter
speech
illustration
photograph
facsimile
blank
advertisement
end-matter
```

A page with an image and a meaningful caption may still require text transcription. Choose the type that best represents its primary content and record the caption.

## 6. Status model

Use a small, explicit status vocabulary:

- `not-started` — no transcription yet;
- `partial` — only part of the page has been reliably read;
- `needs-review` — first-pass transcription exists but has not been visually verified character by character;
- `verified` — directly compared with the source scan;
- `blocked` — source defect prevents reliable completion.

Do not use `verified` merely because OCR confidence is high or because the prose looks grammatical.

## 7. Body transcription rules

### 7.1 Prose

Preserve paragraph sequence. Markdown line wrapping may be normalised for readability, but do not alter paragraph boundaries or sentence content.

### 7.2 Poetry and songs

Preserve each printed poetic line as a separate Markdown line.

Use a hard line break or blank-line convention consistently. Do not convert poetry into prose paragraphs.

### 7.3 Letters

Preserve:

- letter number;
- title;
- salutation;
- date;
- place;
- body;
- closing;
- signature;
- postscript;
- editorial notes.

If a letter starts or ends across pages, the page files must preserve that boundary while the chapter/letter README links the full sequence.

### 7.4 Speeches

Preserve:

- event title;
- venue;
- date;
- introductory publication note;
- speaker labels;
- applause or audience markers if printed;
- section breaks.

### 7.5 Plays and dialogue

Preserve speaker names, stage directions, scene headings, and dialogue order exactly.

### 7.6 Quotations and cited works

Do not replace quotations with a supposedly authoritative online text. Transcribe the quotation as printed in the source being digitised.

### 7.7 Footnotes and marginal notes

Place footnotes after the paragraph or at the bottom of the page file, preserving the printed marker.

### 7.8 Page-end source marker

After final verification, add a source marker:

```html
<!-- மூல ஸ்கேன் பக்கம்: 24; அச்சுப் பக்கம்: 23 -->
```

This creates an auditable link between Markdown and source pagination.

## 8. Images, photographs, and blank pages

### 8.1 Do not invent text for image-only pages

For a full-page image or photograph, record a concise factual description:

```markdown
## காட்சிப் பதிவு

நூலாசிரியரின் முழுப்பக்க புகைப்படம்.
```

Do not identify an unknown person without source support. Do not infer the date, location, or event from appearance alone.

### 8.2 Captions

If a printed caption exists, transcribe it verbatim. Keep the factual image description separate from the printed caption.

### 8.3 Blank pages

Create a page record:

```markdown
## பக்க நிலை

இந்த ஸ்கேன் பக்கம் அச்சு உரையற்ற வெற்றுப் பக்கம்.
```

This prevents false missing-page alarms.

## 9. Contents, indexes, and structural preservation

### 9.1 Transcribe the printed contents pages

The source contents/index must be preserved page by page, even if a cleaner digital index is also created.

### 9.2 Create a structured index

Recommended files:

```text
indexes/contents.md
indexes/chapter-register.md
indexes/page-map.csv
indexes/manifest.md
```

For letters, include:

- letter number;
- title;
- date;
- printed start page;
- scan start page;
- scan end page;
- status.

For chapters, include:

- chapter/malar number;
- title;
- scan range;
- printed-page range;
- text-page count;
- image-page count;
- status.

### 9.3 Preserve discrepancies

If the printed contents page disagrees with the body:

- record both;
- do not silently reconcile them;
- add a documented note in the structured index.

## 10. Chapter, letter, or section READMEs

Each structural unit should have its own README.

Example:

```markdown
# கடிதம் 3764 — சாதனைப் பட்டியலில் விட்டுப் போனவை!

- தொகுதி: 49
- தேதி: ...
- தொடக்கம்: ஸ்கேன் 24 / அச்சுப் பக்கம் 23
- முடிவு: ஸ்கேன் 31 / அச்சுப் பக்கம் 30
- உரைப் பக்கங்கள்: 8 (`verified`)
- நிலை: மூல ஸ்கேனுடன் இறுதி எழுத்து-ஒப்பீடு முடிந்தது

## பக்கங்கள்

1. [ஸ்கேன் 24](../../pages/0024-letter-3764-01.md) — `verified`
...
```

The README is a navigation manifest, not a summary substitute. The complete text remains in the page files.

## 11. Multi-volume rules

### 11.1 One folder per volume

Always use separate volume folders:

```text
volumes/volume-01/
volumes/volume-02/
```

Do not place all volumes’ pages in one shared flat directory.

### 11.2 Independent pagination

Each volume may restart scan numbering at 1. The volume folder prevents filename collisions.

### 11.3 Volume README

Each volume README should contain:

- exact source filename;
- volume title and number;
- scan count;
- printed-page range;
- contents range;
- unit count;
- completed range;
- next unit/page;
- unresolved defects.

### 11.4 Collection-level README

The root README should show:

- available volumes;
- imported source status;
- transcription progress;
- verification progress;
- links to each volume;
- global conventions.

## 12. First-pass workflow

1. Identify source and compute hash.
2. Count all scan pages.
3. Inspect cover, title, publication, and contents pages.
4. Build source metadata.
5. Determine chapter/letter boundaries.
6. Create page manifest for every scan page.
7. Transcribe in manageable batches.
8. Mark first-pass text pages `needs-review`.
9. Mark clearly image-only pages `verified` after visual inspection.
10. Update chapter/letter README and root tracker after every batch.

Do not delay manifest creation until the end. The manifest is how missing pages are detected.

## 13. Final verification workflow

For every text page:

1. Render the source page at readable resolution.
2. Open the existing Markdown beside the scan.
3. Compare from the first character to the last.
4. Check headings, quotations, verse lines, punctuation, and page endings.
5. Correct only what the scan supports.
6. Set:

```yaml
status: "verified"
transcription_method: "direct visual comparison with source scan"
```

7. Remove temporary review notes.
8. Add the source-page comment.
9. Update the chapter/letter README.
10. Recount remaining `needs-review` pages.

## 14. Batch size

For ordinary chapter-based works, use a stable batch of approximately **10 chapters per iteration** unless the chapters are unusually long.

For letters, choose a batch based on page count, not merely letter count. A practical batch is often **25–60 scan pages**.

Each batch report must state:

- units completed;
- scan range;
- text pages verified;
- illustration pages retained;
- changed-file count;
- commit SHA;
- remaining count;
- next batch.

## 15. Git workflow

### 15.1 Keep `main` stable

Use one review branch per batch:

```text
transcribe-volume-49-pages-001-050
verify-chapters-42-51
verify-letters-3764-3770
```

### 15.2 Atomic change set

Prefer one atomic commit containing:

- page files for the batch;
- unit READMEs;
- root/volume tracker;
- no unrelated edits.

### 15.3 Validate before merge

Compare the branch with `main` and verify:

- expected number of files;
- expected page range;
- no skipped pages;
- no duplicated pages;
- no image pages accidentally rewritten;
- no unrelated files;
- branch is the expected number of commits ahead.

### 15.4 Pull request and merge

Use a pull request and squash merge for a clean canonical history.

Suggested commit messages:

```text
Add volume 49 pages 1 through 31
Verify chapters 42 through 51 against source scans
Verify letters 3764 through 3770 against source scans
Complete volume 3 source verification
```

## 16. Automated validation checks

Before merging, run or manually confirm:

- every expected scan page has one page file;
- no two files claim the same scan page;
- `scan_page` values are continuous;
- printed-page mapping is plausible and documented where irregular;
- all Markdown links resolve;
- chapter/letter page counts equal listed pages;
- page statuses match unit README statuses;
- root progress totals equal actual page statuses;
- YAML delimiters are balanced;
- no temporary OCR files were committed;
- no source PDF was accidentally committed unless repository policy explicitly allows it;
- no unresolved review note remains on a `verified` page.

A simple manifest script may be used, but visual source comparison remains mandatory.

## 17. Handling uncertainty

Use a documented convention such as:

```text
[தெளிவில்லை]
[தெளிவில்லை: சொல்லின் தொடக்கம்]
```

or a repository-specific equivalent.

The chosen uncertainty syntax must be documented once and used consistently.

Never hide uncertainty by selecting the most likely word.

## 18. External editions and internet sources

Other editions may be used only to:

- understand a damaged scan;
- identify a likely proper name;
- compare a quotation;
- flag a probable printing or transcription issue.

They must not silently replace the source edition.

When external evidence is used, add an editorial note stating:

- which source was consulted;
- what it suggested;
- whether the printed scan remained unchanged in transcription.

## 19. Handover requirements

At the end of every long session, update `HANDOVER.md` with:

- repository and canonical branch;
- latest `main` commit;
- source filename and scan count;
- completed units and scan range;
- exact remaining units/pages;
- status totals;
- next batch;
- expected changed-file count;
- relevant local render paths, clearly marked as session-specific;
- known source defects;
- known repository inconsistencies;
- required commit message;
- validation checklist;
- stale branches that must not be used;
- a ready-to-paste restart prompt.

Never rely only on chat history for project continuity.

## 20. Definition of done for a book or volume

A work is complete only when:

- all scan pages have page records;
- the printed contents/index is preserved;
- all chapters, letters, or sections have manifests;
- every text page has been visually compared with the scan;
- all text pages are `verified` or explicitly `blocked`;
- illustration and blank pages are accounted for;
- source metadata and hash are recorded;
- no page is missing or duplicated;
- root and volume progress totals reconcile;
- the final branch has been reviewed and merged;
- representative first, middle, and last pages have been re-fetched from `main` and checked.

## 21. Prohibited shortcuts

Do not:

- paste raw OCR as a final transcription;
- summarise a page instead of transcribing it;
- combine several scan pages into one Markdown file;
- omit covers, contents, blank pages, or illustrations;
- silently correct the author’s wording;
- infer missing text from context;
- mark pages verified without opening the scan;
- claim an entire chapter is verified when one text page remains unchecked;
- update progress counts by estimation;
- use a stale branch as the new base;
- overwrite another volume’s files;
- create fabricated `sandbox:` links or source paths.

## 22. Recommended restart prompt for future works

> Start a page-by-page Markdown transcription of the attached Kalaignar work in the specified GitHub repository. Read `KALAIGNAR_WORKS_MARKDOWN_GUIDELINES.md` first. Preserve the complete scan order, printed contents/index, chapter or letter boundaries, original wording, quotations, poems, illustrations, and printed-page mapping. Create one Markdown file per scan page, a manifest for each structural unit, source metadata with a file hash, and a progress tracker. Mark first-pass text pages `needs-review`; mark a text page `verified` only after direct visual comparison with the scan. Use a separate volume folder when the work belongs to a multi-volume collection. Commit in atomic batches through pull requests and maintain `HANDOVER.md` after every substantial session.

## 23. Final principle

The repository should allow a future reader to answer four questions without consulting chat history:

1. What exact source was used?
2. Where is every scan page represented?
3. Which text has been visually verified?
4. What remains uncertain or incomplete?

If the repository cannot answer those four questions, the digitisation is not yet sufficiently documented.
