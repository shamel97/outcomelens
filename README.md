# OutcomeLens

Open, offline, auditable learning analytics for higher education. One HTML file that runs in your browser: it reads a gradebook CSV and shows outcome attainment, assessment quality and a list of students who may need support. No server, no install, no account, and no data leaves your computer.

## Quick start
1. Download `outcomelens.html` and open it in Edge, Chrome or Firefox.
2. Click **Load demo cohort** to see every view with synthetic data, or **Open gradebook CSV** to use your own file (`sample-gradebook-synthetic.csv` shows the format).
3. In **Data and setup**, check each assessment's maximum mark, add outcome tags if you have them, and set the target (default 60%).

## What it shows
| View | Content |
|---|---|
| Overview | Class mean, spread, share at or above the target, distribution, mean per assessment |
| Attainment | Course-outcome and programme-outcome attainment against the target, and the share of students at or above it |
| Assessment quality | Mean, SD, corrected item-total correlation and discrimination per assessment, plus draft improvement notes (ceiling, too hard, bunched marks, low correlation, zero or missing marks) |
| Early warning | Ridge-regression forecast of later marks from early marks, its leave-one-out error against the class average, a "no clear skill" warning, and a support/watch list with reasons |
| Students | Sortable table, profile against the class mean, editable draft feedback comment |

Print (Ctrl+P) gives all views on one report. The support list can be downloaded as a CSV.

## CSV format
First column = student ID. Every other numeric column is an assessment, with raw marks. Columns named name, e-mail, total or grade are ignored. A header such as `Lab report (PLO3 CLO3)` fills the outcome tags automatically; tags are free text, so any naming works. Set the maximum mark of each column in the setup tab (the default is the next multiple of 5 above the highest mark, so check it). Save spreadsheets as CSV; `.xls` files are not read.

## Privacy
The file contains no network requests, no storage and no external libraries. Data stay in memory in your browser tab. Student IDs are masked by default; use the demo cohort for screenshots and recordings. You remain responsible for following your institution's data policy.

## Honest limits
- The forecast uses coursework marks only. On two real classes from one institution (46 and 14 students) it had no skill over simply predicting the class average, and the dashboard said so. Treat it as a prompt for a conversation, not a prediction, and rely on the rules when it shows no skill.
- Draft feedback comes from templates, not a language model. Edit it before use.
- Thresholds (ceiling 85%, hard below 50%, SD below 8, correlation below 0.15, watch rule 1.5 SD) are fixed in v0.1.
- Only exports from one institution have been tested, and there is no question-by-question analysis yet.

## URL switches
`outcomelens.html?demo&tab=warn&light&select=7` opens the demo cohort on a given tab (overview, attain, quality, warn, students, setup).

## Licence
MIT. See `LICENSE`. Contributions and issues are welcome.
