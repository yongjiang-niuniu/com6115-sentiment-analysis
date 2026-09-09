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

The original `Sentiment.py` is unchanged and reads all six files from the **current working directory**. Two public original Rotten Tomatoes files have been recovered; **the exact Nokia pair and sentiment lexicon pair remain missing**. Even the default film-only evaluation loads the Nokia files first.

After obtaining the four original course files listed in [data requirements](data/README.md), place them in the repository root, then:

```bash
cp data/public_rt/rt-polarity.pos .
cp data/public_rt/rt-polarity.neg .
python3 Sentiment.py
```

Windows users can copy the two files with Explorer before running `py Sentiment.py`. Keep the original data encodings. Importing `Sentiment.py` also starts its main script because it has no main guard.

## Reported results / 报告中的结果

These are **historical report values**, not results reproduced during archiving.

| Method | Film test accuracy | Film test F1 (+) | Nokia accuracy | Nokia F1 (+) |
|---|---:|---:|---:|---:|
| Naïve Bayes | 0.7696 | 0.7667 | 0.5902 | 0.6540 |
| Dictionary baseline | 0.6808 | 0.6512 | 0.7970 | 0.8492 |
| Improved dictionary | 0.6611 | 0.6161 | 0.8083 | 0.8563 |

报告正文称规则改进提高了电影测试效果，但表 2/3 显示 `0.6808 → 0.6611`。归档保留原始数字并标注这个不一致；代码没有固定随机种子，不能把这些数值当作同一次固定划分上的改进证明。完整表格见 [结果说明](docs/RESULTS.md)。

## Validation and limits

Syntax compilation passed. A controlled check invoked the **original Bayes functions** on 64 real public RT training examples and 20 held-out examples. It completed successfully without network access or synthetic data. This only checks that those functions execute; the full script, dictionary methods and historical metrics were not reproduced because original data dependencies are incomplete.

The submitted behavior is preserved, including an unseeded split, sentence-keyed dictionaries that can overwrite duplicate/empty records, direct probability products that can underflow, and the original missing-count smoothing. The improved rules inspect one preceding token, so they do not model general negation scope or discourse structure.

## Archive and attribution

Blackboard: **Assignment – Sentiment Analysis, Attempt 1, 20 November 2025 at 22:17 UTC+8**. Both original attachment checksums are recorded in [provenance](docs/PROVENANCE.md). New commits represent actual archival work on the recovery date; no development history is invented.

The Python file retains coursework scaffold comments and TODO markers. This archive documents the submitted implementation and report, without asserting that every starter-code line was independently authored. The public RT data retains its original Pang/Lee attribution. Course materials and submitted work remain private; no new redistribution license is asserted.
