# Sentiment analysis documentation

Start with the [project overview](../README.md) for the experiment, supported command and summary results.

| Guide | Use it to |
| --- | --- |
| [Getting started](../README.md#getting-started) | Run the unchanged script from the required data directory. |
| [Data and attribution](../data/README.md) | Check the six inputs, encodings, counts and original dataset sources. |
| [Results and verification](RESULTS.md) | Compare historical report tables with the separate archive execution check. |
| [Submitted contributions](CONTRIBUTIONS.md) | Distinguish the submitted additions from the official starter scaffold. |
| [Submission provenance](PROVENANCE.md) | Locate original attachment hashes and supporting-material records. |
| [Original report](../reports/COM6115_Sentiment_Analysis_Coursework_Report.pdf) | Read the complete submitted discussion and tables. |

## Verification evidence

- [Full script run](validation/full_run.json), [console output](validation/full_script_output.txt) and [initial random state](validation/initial_random_state.json): the later check using all six official course files.
- [Reported metrics](reported_metrics.csv): a transcription of report values, separate from execution output.
- [Earlier bounded check](validation/initial_smoke.json): an earlier recovery-stage check with a smaller data scope; it does not describe the current data availability.

Original source and datasets retain their existing locations because the script depends on its working directory. Documentation changes do not alter the model, data split or historical evidence.
