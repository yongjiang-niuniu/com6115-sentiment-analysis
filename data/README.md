# Required data and recovery status

`Sentiment.py` opens these exact filenames relative to the working directory. They were not attached to the recovered Blackboard submission.

| Filename | Role | Status |
|---|---|---|
| `rt-polarity.pos` | Positive film snippets | Public original sentence polarity v1.0 recovered in `public_rt/` |
| `rt-polarity.neg` | Negative film snippets | Public original sentence polarity v1.0 recovered in `public_rt/` |
| `nokia-pos.txt` | Positive Nokia reviews | Exact course file not recovered |
| `nokia-neg.txt` | Negative Nokia reviews | Exact course file not recovered |
| `positive-words.txt` | Positive sentiment lexicon | Exact course file not recovered |
| `negative-words.txt` | Negative sentiment lexicon | Exact course file not recovered |

The loader uses ISO-8859-1 for both RT files, negative Nokia and both word lists. Positive Nokia uses the platform's default text encoding. Word-list entries are stripped and empty lines or lines starting with `;` are ignored. The original loader retains empty review strings and stores sentences as dictionary keys; changing those details would change historical behavior.

## Public original RT dependency

The report names the Rotten Tomatoes polarity dataset, and the source requests the exact `rt-polarity.pos` / `.neg` filenames. These identify the [Cornell sentence polarity dataset v1.0](https://www.cs.cornell.edu/people/pabo/movie-review-data/): 5,331 positive and 5,331 negative sentence/snippet records. The [original README](public_rt/rt-polaritydata.README.1.0.txt) and original file bytes are retained.

Source: [Cornell archive](https://www.cs.cornell.edu/people/pabo/movie-review-data/rt-polaritydata.tar.gz), downloaded 9 September 2026. The [download manifest](../docs/provenance/public-rt.json) records hashes. This was recovered from the public original distribution, **not** Blackboard; no original course-data checksum exists for byte-for-byte comparison.

Attribution: Bo Pang and Lillian Lee, *Seeing stars: Exploiting class relationships for sentiment categorization with respect to rating scales*, ACL 2005. Preserve the dataset version and original attribution when using it.

## Unresolved original files

The report and code do not identify a URL or checksum for the pre-split Nokia files or lexicons. The [UIC opinion lexicon page](https://www.cs.uic.edu/~liub/FBS/sentiment-analysis.html) distributes positive and negative word lists, but the submitted material does not establish that exact release as the original coursework dependency. No guessed replacement or other student's data preparation has been added.

Recover these four original files from the course resources or original project folder to run the unchanged script. Their labels, preprocessing and lexicon version matter for reproducing the report. No synthetic dataset is included as a substitute.
