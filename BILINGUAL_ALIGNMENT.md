# Tamil–English Bilingual Alignment Audit

This record compares the source structure of Kalaignar M. Karunanidhi's Tamil *தொல்காப்பியப் பூங்கா* with its published English translation, *The Flower-garden of Tolkāppiyam*, to detect possible omissions introduced during repository transcription.

## Scope

- Tamil edition: 100 மலர்கள், preserved from the 537-scan source edition.
- English edition: 100 Blossoms, preserved from the 281-scan source edition.
- Alignment keys checked: chapter order, title correspondence, அதிகாரம் / Atikāram, இயல் / Iyal, and நூற்பா / verse references.
- Purpose: identify missing repository transcription, not to judge translation quality or force the two published books to have identical editorial treatment.

## Overall result

All **100 Tamil மலர்கள் have a corresponding English Blossom in the same sequence**. No missing Blossom or missing chapter-level source block was found in the repository.

The அதிகாரம் / இயல் progression is structurally consistent between the two editions. The printed verse mappings agree for **97 of 100 Blossoms**. The three differences below are attributable to the published editions' indexing or exposition, not to missing repository transcription.

## Edition-level verse-map differences

| Blossom | Tamil | English | Tamil printed index | English printed index | Finding |
|---:|---|---|---:|---:|---|
| 18 | முதல் பொருள் | Mutal Poruḷ | 5 | 4, 5 | Not a transcription omission. The Tamil chapter body includes both நூற்பா 4 and 5; its printed contents table lists only 5. |
| 86 | உவமை அறிவோம் | Know Your Simile | 2 | 1, 2 | Not a transcription omission. The Tamil chapter includes நூற்பா 1 and later நூற்பா 2; its printed contents table lists only 2. |
| 93 | அன்றே வளர்ந்திருந்த அறிவியல் | Science that had Developed Then | 27, 28, 29, 30 | 27, 28, 29, 30, 31, 32 | Not a transcription omission. The Tamil exposition explicitly quotes 27–30 and discusses the sensory classification continued in 31–32; the English edition indexes the expanded 27–32 range. |

## Structural exception

**Blossom 24** is an explanatory interlude. The Tamil contents table carries no அதிகாரம் / இயல் / நூற்பா mapping for it, and the English edition likewise does not require an invented Tolkāppiyam verse reference. This is an intentional structural exception, not missing data.

## Conclusion

The bilingual structural comparison found **no evidence that repository transcription skipped a Blossom, chapter, or mapped Tolkāppiyam source unit**.

The remaining possible bilingual work is a different task: paragraph/episode-level translation-completeness alignment to identify places where the 2009 English translator abridged, expanded, combined, or reorganized material relative to the 2003 Tamil edition. Such differences should be documented as translation/editorial differences and should not be silently used to alter either source-faithful transcription.

## Repository references

- Tamil contents map: [`indexes/contents.md`](indexes/contents.md)
- Tamil transcription status: [`README.md`](README.md)
- English contents map: [`english-translation/contents/index.md`](english-translation/contents/index.md)
- English second-pass fidelity audit: [`english-translation/FIDELITY.md`](english-translation/FIDELITY.md)
