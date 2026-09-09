# Report metrics and archive verification

## Historical report evidence

The following values are transcribed from report tables 1–3 (PDF pages 2–4). They have **not** been independently reproduced. A machine-readable copy is in [reported_metrics.csv](reported_metrics.csv).

| Method | Dataset | Accuracy | Precision + | Recall + | Precision − | Recall − | F1 + |
|---|---|---:|---:|---:|---:|---:|---:|
| Naïve Bayes | Films train | 0.8899 | 0.8985 | 0.8792 | 0.8818 | 0.9007 | 0.8887 |
| Naïve Bayes | Films test | 0.7696 | 0.7771 | 0.7566 | 0.7624 | 0.7826 | 0.7667 |
| Naïve Bayes | Nokia | 0.5902 | 0.7984 | 0.5538 | 0.3942 | 0.6750 | 0.6540 |
| Dictionary | Films train | 0.6492 | 0.6792 | 0.5670 | 0.6278 | 0.7317 | 0.6180 |
| Dictionary | Films test | 0.6808 | 0.7099 | 0.6015 | 0.6598 | 0.7587 | 0.6512 |
| Dictionary | Nokia | 0.7970 | 0.8837 | 0.8172 | 0.6383 | 0.7500 | 0.8492 |
| Improved dictionary | Films train | 0.6556 | 0.6864 | 0.5768 | 0.6331 | 0.7349 | 0.6268 |
| Improved dictionary | Films test | 0.6611 | 0.6832 | 0.5610 | 0.6465 | 0.7553 | 0.6161 |
| Improved dictionary | Nokia | 0.8083 | 0.8994 | 0.8172 | 0.6495 | 0.7875 | 0.8563 |

The report text describes a film-test improvement from rule extensions, but its displayed baseline/improved test accuracies are `0.6808` and `0.6611`. These do not demonstrate that improvement. The random split is unseeded and split assignments were not saved; a paired comparison cannot be established. The PDF and values remain unchanged.

The submitted default main calls only film-test Bayes, film-test baseline dictionary and informative-word output. The report's training, Nokia and improved-rule evaluations require other calls that are commented out in the submitted file. The default Bayes prior is 0.5; the commented Nokia Bayes call specifies 0.7. Original data and experiment settings would be needed to reconstruct the full tables.

## Complete submitted-script verification on 9 September 2026

After recovering the official course package, the unchanged script ran to completion under Python 3.12.14 using all six original data files in an isolated copy. Network connections were blocked and none were attempted. No seed override was applied; the initial random state was captured before execution.

| Check | Result |
|---|---|
| Script exit | 0, completed |
| Training / test sentence keys | 9,547 / 1,116 |
| Training/test overlapping keys in this run | 0 |
| Nokia keys loaded / unique lexicon keys | 266 / 6,786 |
| Film-test Bayes accuracy / F1 (+) | 0.7796 / 0.7842 |
| Film-test baseline dictionary accuracy / F1 (+) | 0.6756 / 0.6533 |

These are **new verification results** on an unseeded split, not reproduced historical tables. They cover the two active classification calls and informative-word output. Nokia data loaded successfully, but the Nokia evaluation and improved-rule calls remained commented out and were not executed. Original source and data bytes remained unchanged.

Evidence: [full run record](validation/full_run.json), [original console output](validation/full_script_output.txt), [initial random state](validation/initial_random_state.json). The random-state record belongs only to this new archive verification run.

## Earlier bounded check

Python 3.12.14 compiled the original source successfully. A bounded check loaded only the original function definitions, avoiding top-level file loading, then called `trainBayes`, `testBayes` and `mostUseful` on public original RT records: first 32 nonempty LF-delimited records per polarity for training and the next 10 per polarity held out. No synthetic data or full-corpus training was used; network connections were blocked.

The 64-training/20-held-out check completed successfully before the official supporting files were recovered. It verified those original functions, not report accuracy. Original code bytes were unchanged; error-example printing was suppressed in its isolated namespace. The full-script check above supersedes that earlier data-gap status.

[Initial smoke record](validation/initial_smoke.json) records its acquisition-time data gap and limited scope. No mirror implementation or new model code was added.

## Preserved implementation limits

- Splits use random decisions without a fixed seed. Dictionaries keyed by full sentence can overwrite duplicate/empty records, and split overlap is not explicitly checked.
- Bayes multiplies probabilities directly; underflow can occur. Missing class counts are set to 1 without standard vocabulary-adjusted Laplace denominators. These original choices are preserved.
- Baseline token matching is case-sensitive. Improved dictionary scoring lowercases tokens and checks just the preceding token; the tokenizer retains apostrophes, so the `n't` rule does not generally capture whole contractions.
- The implementation prints positive-class F1, not macro-F1. Error examples and ranked words are report diagnostics, not a saved trained model.
