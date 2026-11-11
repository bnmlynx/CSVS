# Clinical Research Skills & Critical Appraisal

A self-paced e-learning course for clinical vascular scientists, produced for **CSVS — The College and Society for Clinical Vascular Science**.

It takes learners from forming a research question through to publishing their findings. The course has nine modules with worked case studies, then a capstone research-design exercise and a 20-question knowledge check.

## Course content

| # | Module | Covers |
|---|--------|--------|
| 1 | Identifying a Research Question | Where questions come from; research vs audit vs service evaluation; NIHR and HRA; the FINER framework |
| 2 | Conducting a Literature Review | Search strategy, synthesis, critical appraisal frameworks, validity and advanced critique |
| 3 | Research Question & Hypothesis | PICO (with an interactive question builder), types of quantitative question, null/alternative hypotheses, deductive vs inductive reasoning |
| 4 | Research Methodologies | Matching method to question, quantitative and qualitative research, study design hierarchy, sampling |
| 5 | Approvals for Clinical Research | Sponsorship, study documents, IRAS, REC review and HRA approval, site capacity and capability |
| 6 | Ethics in Clinical Research | Ethical principles and how they apply in practice |
| 7 | Research Funding | Finding and applying for funding |
| 8 | Statistics for Researchers | Core statistical concepts, with a link to the NIHR Statistics Group |
| 9 | Dissemination of Research | Conferences, publication and sharing results |

Each module ends with an expandable **case study** of multiple-choice questions. Learners get feedback on each answer straight away.

After the modules come:

- **Integrated Research Design Exercise**: a capstone that brings all nine modules together.
- **Knowledge Check**: 20 questions covering every module. Unanswered questions count as incorrect. Results show the overall score and a breakdown by module, and learners can retake it as many times as they like.

## Running it

There is no build step and nothing to install. The whole course is one static HTML file.

```bash
open index.html          # macOS
# or serve it locally
python3 -m http.server 8000   # then visit http://localhost:8000
```

To host it, upload `index.html` and `csvs.png` together to any static host (GitHub Pages, Netlify, an intranet web server, etc.).

## Project structure

```
.
├── index.html   # All content, styles and JavaScript for the course
├── csvs.png     # CSVS logo shown in the header (hidden if the file is missing)
└── README.md
```

Inside `index.html`:

- **Pages**: each module, the capstone, the knowledge check and the results screen is its own `.page` section. `goToPage()` moves between them and keeps the progress bar in step.
- **Case studies**: `toggleCase()` opens and closes a case study, and `checkCaseStudy()` marks its answers.
- **Interactive tools**: the FINER checklist (`updateFiner()`) and the PICO question builder.
- **Knowledge check**: `countAnswered()` and `updateAnsweredCount()` track progress. The submit handler works out the score and the per-module breakdown.

Nothing is stored or sent anywhere. Progress and scores only exist in the open browser tab and are lost when it is refreshed.

## Editing content

- Each module is marked in the HTML with a comment banner such as `<!-- PAGE 0: MODULE 1 — Identifying a Research Question -->`, so you can search for `MODULE <n>` to find the one you want to change.
- To add or change a knowledge-check question, edit its markup and keep the `TOTAL` question count in the script in line with it, so scoring and the "Answered: x of 20" counter stay correct.
- Open the file in a browser after editing and click through the pages you changed. There are no automated tests.
