# COM6115 · Sentiment Analysis

谢菲尔德大学 COM6115 情感分析课程项目，比较 **朴素贝叶斯、词典评分和加入否定/程度规则的词典模型**，研究电影评论内的分类效果以及迁移到 Nokia 产品评论时的变化。

This private coursework archive preserves Yongjiang Liu's official submitted Python file and report. It compares a unigram Naïve Bayes classifier with lexicon scoring and local negation/intensity rules, including cross-domain analysis.

[正式报告 / Report](reports/COM6115_Sentiment_Analysis_Coursework_Report.pdf) · [数据依赖 / Data](data/README.md) · [提交来源 / Provenance](docs/PROVENANCE.md) · [指标与验证 / Results](docs/RESULTS.md)

## What the code contains

| Component | Submitted implementation |
|---|---|
| Data loading | Six named text files; approximate random 90/10 film split, plus Nokia review labels and positive/negative word lists |
| Naïve Bayes | Regex unigram tokens, class word-frequency probabilities, direct probability multiplication and class priors |
| Dictionary baseline | Sum `+1` / `-1` for lexicon matches; classify positive at score ≥ 1 |
| Improved dictionary | Lowercase matching; inspect the immediately preceding token to reverse, double or halve a sentiment word's score |
| Evaluation | Accuracy, positive/negative precision and recall, and positive-class F1 |
| Feature inspection | Rank vocabulary by positive versus negative conditional probabilities; print 100 words at each end |

The submitted main script runs **film test Naïve Bayes, film test dictionary baseline and informative-word output**. Nokia evaluation, training-set evaluation and all improved-rule calls are present but commented out. Their presence in the report does not mean the default command runs every reported experiment.

## Run / 运行

Only Python's standard library is imported; no pip packages are required. Archive checks used Python **3.12.14**.

The original `Sentiment.py` is unchanged. **All six required data files have been recovered from the official Blackboard course package** and are in `data/course/`. Run from that directory because the script reads files from its current working directory:

```bash
cd data/course
python3 ../../Sentiment.py
```

On Windows, use `py ../../Sentiment.py` from the same directory. Keep the original data encodings. Importing `Sentiment.py` also starts its main script because it has no main guard. The default film-only evaluation still loads the Nokia files.

## Reported results / 报告中的结果

These are **historical report values**, not results reproduced during archiving.

| Method | Film test accuracy | Film test F1 (+) | Nokia accuracy | Nokia F1 (+) |
|---|---:|---:|---:|---:|
| Naïve Bayes | 0.7696 | 0.7667 | 0.5902 | 0.6540 |
| Dictionary baseline | 0.6808 | 0.6512 | 0.7970 | 0.8492 |
| Improved dictionary | 0.6611 | 0.6161 | 0.8083 | 0.8563 |

报告正文称规则改进提高了电影测试效果，但表 2/3 显示 `0.6808 → 0.6611`。归档保留原始数字并标注这个不一致；代码没有固定随机种子，不能把这些数值当作同一次固定划分上的改进证明。完整表格见 [结果说明](docs/RESULTS.md)。

## Validation and limits

On 9 September 2026, the **complete unchanged submitted script ran successfully using all six official course files** in an isolated copy. Its new random split contained 9,547 training and 1,116 test sentence keys. Film-test accuracy was **0.7796 for Bayes** and **0.6756 for the dictionary baseline**. Source and data bytes were unchanged; no external connections occurred.

These are new validation results, not a recreation of the historical report's split. The original script does not fix a random seed. Its commented Nokia and improved-rule evaluations were not executed. The raw output, random state and [verification record](docs/RESULTS.md) are retained separately from the reported metrics. A preliminary small real-data Bayes check is also recorded as an earlier validation step.

The submitted behavior is preserved, including an unseeded split, sentence-keyed dictionaries that can overwrite duplicate/empty records, direct probability products that can underflow, and the original missing-count smoothing. The improved rules inspect one preceding token, so they do not model general negation scope or discourse structure.

## Archive and attribution

Blackboard: **Assignment – Sentiment Analysis, Attempt 1, 20 November 2025 at 22:17 UTC+8**. Both original attachment checksums are recorded in [provenance](docs/PROVENANCE.md). New commits represent actual archival work on the recovery date; no development history is invented.

The official starter script is preserved separately in `course_materials/starter/`. Comparing it with the submitted file identifies added lexicon loading, evaluation metrics, dictionary error output, the improved-rule function and enabled diagnostic calls. The base Bayes learner and other supplied helpers are course scaffolding. [Contribution notes](docs/CONTRIBUTIONS.md) describe the difference.

RT data retains Pang/Lee attribution; the course lexicons retain their Hu/Liu citation headers. Course materials and submitted work remain private; no new redistribution license is asserted.
