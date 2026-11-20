# Recall ranking evaluation for 80 fixed queries

Linger ran these development experiments on October 30–31, 2026 against an isolated copy of one library with **145 valid images**. The **80-query** test set included 76 positive queries referring to 25 distinct targets and four queries without a target. Only 24 images received machine analysis. Most queries were written while viewing the targets; four came from the user.

## Candidate rankings before model review

Each cell counts how often the target was within the first K candidates across the same 76 positive queries. The four negative cases have no target rank.

| Stage | Top 1 | Top 5 | Top 24 | Top 48 |
| --- | ---: | ---: | ---: | ---: |
| Before automatic analysis | 50/76 | 62/76 | 66/76 | 75/76 |
| Text matches first (rejected) | 39/76 | 47/76 | 66/76 | 75/76 |
| Guarded text + image fusion | 50/76 | 62/76 | 66/76 | 75/76 |
| Shorter analysis prompt | 50/76 | 62/76 | 66/76 | 75/76 |
| Text semantics (experiment) | 50/76 | 62/76 | 69/76 | 74/76 |
| Text semantics + protected pool (experiment) | 50/76 | 62/76 | 69/76 | 75/76 |

Text-first ordering pushed relevant images down without changing top-24 coverage. The final experiment recovered top-48 coverage by allowing stronger text matches to move only within the original top-48 pool. Its three additional top-24 hits all referred to one target image.

This is a repeated regression set from one library. It measures candidate coverage before optional model review. It does not establish an independent user's success rate, absent-target accuracy, or performance on large libraries. The last two rows are experimental ranking stages. The published ranks let you recalculate the table. Reproducing the original experiment would require the private images, query text, and other inputs.

[Official article and methodology](https://withlinger.com/resources/how-linger-recall-evolved/) · [80 anonymous query ranks](https://withlinger.com/assets/resources/recall-evolution/query-ranks.csv) · [Stage totals](https://withlinger.com/assets/resources/recall-evolution/experiment-summary.csv) · [Data definitions](https://withlinger.com/assets/resources/recall-evolution/data-notes.md)
