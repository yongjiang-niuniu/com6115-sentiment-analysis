# Complete official data and source attribution

All six files are now recovered from the official Blackboard `Code_data.zip` instruction attachment. They are in `data/course/`, unchanged. They are supporting course materials, separate from the user's submitted report and code.

| Filename | Role | Status |
|---|---|---|
| `rt-polarity.pos` | Positive film snippets | 5,331 nonempty LF-delimited records |
| `rt-polarity.neg` | Negative film snippets | 5,331 nonempty LF-delimited records |
| `nokia-pos.txt` | Positive Nokia reviews | 193 nonempty LF-delimited records |
| `nokia-neg.txt` | Negative Nokia reviews | 79 nonempty LF-delimited records |
| `positive-words.txt` | Positive sentiment lexicon | 2,006 entries after comments/blank lines are skipped |
| `negative-words.txt` | Negative sentiment lexicon | 4,783 entries after comments/blank lines are skipped |

The source stores sentence text and lexicon words as dictionary keys, so effective counts can differ because of duplicate or empty records. The verification run loaded 266 Nokia keys and 6,786 unique lexicon keys. [Course-file hashes and provenance](../docs/provenance/course-materials.json) record the exact files.

The loader uses ISO-8859-1 for both RT files, negative Nokia and both word lists. Positive Nokia uses the platform's default text encoding. Word-list entries are stripped and empty lines or lines starting with `;` are ignored. The original loader retains empty review strings and stores sentences as dictionary keys; changing those details would change historical behavior.

## Public original RT dependency

The report names the Rotten Tomatoes polarity dataset, and the source requests the exact `rt-polarity.pos` / `.neg` filenames. These identify the [Cornell sentence polarity dataset v1.0](https://www.cs.cornell.edu/people/pabo/movie-review-data/): 5,331 positive and 5,331 negative sentence/snippet records. The [original README](public_rt/rt-polaritydata.README.1.0.txt) and original file bytes are retained.

Source: [Cornell archive](https://www.cs.cornell.edu/people/pabo/movie-review-data/rt-polaritydata.tar.gz), downloaded 9 September 2026 before the official course package was recovered. The [public download manifest](../docs/provenance/public-rt.json) records that earlier acquisition. Subsequent comparison confirms **both course RT files match these Cornell originals byte-for-byte**. Both provenance paths are retained.

Attribution: Bo Pang and Lillian Lee, *Seeing stars: Exploiting class relationships for sentiment categorization with respect to rating scales*, ACL 2005. Preserve the dataset version and original attribution when using it.

## Course lexicon and Nokia files

The course lexicon headers explicitly cite Minqing Hu and Bing Liu, *Mining and Summarizing Customer Reviews* (KDD 2004), and Bing Liu, Minqing Hu and Junsheng Cheng, *Opinion Observer: Analyzing and Comparing Opinions on the Web* (WWW 2005). Their headers point to the [UIC opinion lexicon page](https://www.cs.uic.edu/~liub/FBS/sentiment-analysis.html). The exact Blackboard copies are preserved with those headers.

The Nokia pair is preserved exactly as supplied by the course. Its upstream review-selection and label-preparation history is not established by these files. No guessed replacement, synthetic example set or other student's preparation was substituted.
