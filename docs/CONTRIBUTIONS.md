# Submitted work compared with the official starter

The official course package includes `course_materials/starter/Sentiment.py` (9,745 bytes). The user's official submission is root `Sentiment.py` (15,878 bytes). Both files are preserved unchanged, making the coursework additions reviewable without inventing development history.

| Area | Difference visible in the submitted file |
|---|---|
| Lexicon loading | Populate positive/negative lists, stripping entries and ignoring blank/comment lines |
| Evaluation | Add accuracy, positive/negative precision and recall, and positive-class F1 to Bayes and dictionary evaluators |
| Error diagnostics | Set `PRINT_ERRORS=1`; add dictionary misclassification output |
| Improved rules | Add `testDictionaryImproved`, with lowercase lookup and immediately preceding negation/intensifier/diminisher adjustments |
| Experiment calls | Enable film-test dictionary scoring and informative-word output; add commented improved-rule calls |
| Report | Submit analysis of in-domain/cross-domain performance, informative vocabulary and model-specific errors |

The underlying Bayes learner, dataset split, baseline scoring structure and informative-word helper are supplied course scaffolding. They are not presented as independently invented algorithms. The submitted changes are consistent with the assessment tasks described in the recovered brief.

Compare the preserved files locally:

```bash
git diff --no-index course_materials/starter/Sentiment.py Sentiment.py
```

This is a comparison of recovered starter and final files. It does not establish the intermediate sequence or authorship timestamps of edits. The new Git commits record actual archive work only.
