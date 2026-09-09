# Sentiment Analysis · COM6115

A comparison of three approaches to binary sentiment classification: unigram Naïve Bayes, sentiment-lexicon scoring and lexicon rules for negation and intensity. The project studies both movie-review classification and transfer to Nokia product reviews, with error examples and informative-word analysis.

中文概述：本项目比较朴素贝叶斯、词典评分与简单语言规则在电影评论和 Nokia 产品评论中的效果。完整课程数据、原始代码、报告及验证记录均已保存，历史报告指标与归档时的运行结果分别列明。

## Project at a glance

| Field | Details |
| --- | --- |
| Course | COM6115, University of Sheffield |
| Project type | Individual NLP coursework; supervised and rule-based text classification |
| Technology | Python standard library, unigram features, sentiment lexicons |
| Inputs | Positive/negative film snippets, Nokia reviews and two sentiment word lists |
| Status | Submitted code and report preserved; all six required data files available; default script execution verified |

## What it does

The program builds word-probability tables from an approximate 90/10 random film-data split, evaluates sentiment predictions and prints accuracy, class-specific precision/recall and positive-class F1. It also displays misclassified sentences and the 100 strongest vocabulary predictors at each end of the polarity ranking.

The submitted default command runs **film-test Naïve Bayes, film-test dictionary scoring and informative-word output**. Nokia evaluation, training-set evaluation and improved-rule calls are included but commented out. The report discusses those additional experiments; they are not all executed by the default command.

## Repository guide

| Location | Contents |
| --- | --- |
| [Sentiment.py](Sentiment.py) | Unchanged submitted implementation and default experiment calls |
| [data/course/](data/course/) | All six official input files used by the loader |
| [data/README.md](data/README.md) | Dataset counts, encodings and attribution |
| [course_materials/](course_materials/) | Official brief and starter code for comparison with the submitted work |
| [Report](reports/COM6115_Sentiment_Analysis_Coursework_Report.pdf) | Original ten-page analysis and historical results |
| [docs/](docs/README.md) | Results, contribution comparison, provenance and verification evidence |

## Getting started

Use Python 3; archive execution was verified with **Python 3.12.14**. The script imports only the standard library, so no pip installation is needed.

From the repository root:

```sh
cd data/course
python3 ../../Sentiment.py
```

On Windows, run `py ../../Sentiment.py` from the same directory. The working directory matters because the original loader opens data filenames relative to it. Keep the supplied file encodings. All six files are loaded even when only film classification is enabled.

Expect console output containing classification errors, metrics and word rankings. This is an experiment script, not an interactive prediction service or saved-model package. Importing it also executes its main code because it has no main guard. See the [data guide](data/README.md) for exact file requirements.

## Design and method

| Method | Main idea | Role in the comparison |
| --- | --- | --- |
| Naïve Bayes | Tokenize with a regular expression, estimate class word probabilities and combine them with a class prior. | Learn domain-specific sentiment associations from labelled film snippets. |
| Dictionary baseline | Sum positive and negative word-list matches, using a threshold of 1. | Classify without learning sentiment weights from the film training set. |
| Improved dictionary | Lowercase tokens and inspect the preceding token to reverse, double or halve a matched sentiment score. | Explore local negation, intensifiers and diminishers. |

The evaluation uses positive and negative labels; the reported F1 is for the **positive class**, not macro-F1. The [contribution comparison](docs/CONTRIBUTIONS.md) identifies the student's additions to the supplied Bayes/data-loading scaffold.

## Results and verification

**Historical report results:**

| Method | Film-test accuracy | Film-test F1 (+) | Nokia accuracy | Nokia F1 (+) |
| --- | ---: | ---: | ---: | ---: |
| Naïve Bayes | 0.7696 | 0.7667 | 0.5902 | 0.6540 |
| Dictionary baseline | 0.6808 | 0.6512 | 0.7970 | 0.8492 |
| Improved dictionary | 0.6611 | 0.6161 | 0.8083 | 0.8563 |

**Archive execution check:** on 9 September 2026, the unchanged script completed with all six official files under Python 3.12.14. Its new random split contained 9,547 training and 1,116 test sentence keys. Film-test accuracy was **0.7796 for Bayes** and **0.6756 for the dictionary baseline**. The original bytes were unchanged, and no network connection was attempted.

That run verifies the active submitted workflow; it does not reproduce the historical split or the commented Nokia/improved-rule experiments. The [results guide](docs/RESULTS.md) contains complete tables, output and the captured random state. This documentation refresh checks navigation and preservation; it does not rerun or replace those experiments.

## Limitations

- The random split is unseeded. Sentence-keyed dictionaries can overwrite duplicate or empty records, and the script does not enforce train/test uniqueness.
- Direct probability multiplication can underflow; missing-count handling is the original course implementation rather than conventional vocabulary-adjusted Laplace smoothing.
- Rules inspect only one preceding token, so they do not model general negation scope or discourse. The baseline is case-sensitive.
- The report describes a film-test improvement from the rules, but its tables show accuracy falling from 0.6808 to 0.6611. Those values and the unpaired random splits do not establish that claimed improvement.

## Attribution and provenance

Yongjiang Liu's submitted additions include lexicon loading, evaluation metrics, dictionary error diagnostics, local language rules and experiment/report analysis. The Bayes learner and other supplied helpers remain credited as course scaffolding.

The RT data retains Pang/Lee attribution; the lexicons retain their Hu/Liu citation headers. Original code, report and course materials remain unchanged in this private repository. [Provenance](docs/PROVENANCE.md) records the official submission, supporting materials and file hashes; [data attribution](data/README.md) records the dataset sources.
