# Sheffield Hallam University — PhD Thesis LaTeX Template

A structured, parameter-driven LaTeX template for PhD candidates at Sheffield Hallam University (SHU). Developed by **Raymond Mawanda**, adapted from the PhD thesis of **Muhammad Aitsam** — see [Credits](#credits) for full attribution.

---

## Table of Contents

1. [Requirements](#requirements)
2. [Getting Started](#getting-started)
3. [Project Structure](#project-structure)
4. [Step-by-Step: How to Personalise the Template](#step-by-step-how-to-personalise-the-template)
   - [Step 1 — Fill in your thesis metadata](#step-1--fill-in-your-thesis-metadata)
   - [Step 2 — Add your ethics approvals](#step-2--add-your-ethics-approvals)
   - [Step 3 — Write your front matter](#step-3--write-your-front-matter)
   - [Step 4 — Write your chapters](#step-4--write-your-chapters)
   - [Step 5 — Add appendices](#step-5--add-appendices)
   - [Step 6 — Manage your bibliography](#step-6--manage-your-bibliography)
5. [AI Disclosure (Optional)](#ai-disclosure-optional)
6. [Compiling the Thesis](#compiling-the-thesis)
7. [Files You Should NOT Edit](#files-you-should-not-edit)
8. [SHU Submission Checklist](#shu-submission-checklist)
9. [Troubleshooting](#troubleshooting)
10. [Credits](#credits)

---

## Requirements

- **Overleaf** (recommended) — no local installation needed. Open this project directly in your browser.
- OR a local LaTeX distribution: **TeX Live 2020+** or **MiKTeX** with `pdflatex`.
- The `PhDThesisPSnPDF.cls` class file is already included in the project root.

---

## Getting Started

1. **Copy this GitHub repository URL**:
   `https://github.com/SHU-SIT-Lab/PhD_Thesis_Template_SheffieldHallam.git`
2. **Open [Overleaf](https://www.overleaf.com)** and sign in to your account.
3. From the Overleaf dashboard, click **New Project** → **Import from GitHub**.
4. **Paste the repository URL** and click **Import**. Overleaf will create a new project from the template.
5. Once the project opens, **set `thesis.tex` as the main file**: right-click it in the file tree → *Set as Main File*.
6. Open `config/thesis-info.tex` — this is the **only file you need to edit first**. Fill in your name, thesis title, supervisors, and other details.
7. Click **Recompile** to confirm the title page and front matter render correctly.
8. Begin writing your chapters.
## Project Structure

```
 thesis.tex                  <- Main file. Ties everything together. Do not edit content here.
 PhDThesisPSnPDF.cls         <- Thesis class file. Do not edit.
 SHU_crest.jpg               <- University crest used on the title page.
 README.md                   <- This file.

 config/
   thesis-info.tex           <- YOUR DETAILS GO HERE (title, name, supervisors, etc.)
   ethics-approvals.tex      <- YOUR ETHICS APPROVAL ROWS GO HERE
   preamble.tex              <- Extra LaTeX packages/settings (advanced users only)

 frontmatter/
   abstract.tex              <- Your abstract (300 words max recommended)
   acknowledgements.tex      <- Acknowledgements
   declaration.tex           <- Auto-generated declaration (do not edit)
   publications.tex          <- List of publications arising from the thesis
   quote.tex                 <- Optional opening quote

 chapters/                   <- One .tex file per chapter
 appendices/                 <- One .tex file per appendix

 bib/
   bibliography.bib          <- Your BibTeX references
```

---

## Step-by-Step: How to Personalise the Template

### Step 1 — Fill in your thesis metadata

Open **`config/thesis-info.tex`**. This is the **Single Edit Source** — changing values here automatically updates the title page, declaration, and all front matter. You should not need to touch any other file for your personal details.

| Field | What to enter | Example |
|---|---|---|
| `\ThesisTitle` | Full title of your thesis | `The Role of X in Y` |
| `\CandidateName` | Your full name | `Jane A. Smith` |
| `\degreetitle` | Degree being sought | `Doctor of Philosophy` |
| `\degreedate` | Month and year of submission | `September 2026` |
| `\AwardName` | Award name for declaration | `Doctor of Philosophy` |
| `\SubmissionDate` | Submission date for declaration | `September 2026` |
| `\CollegeName` | Your college/department | `College of Business, Technology and Engineering` |
| `\DirectorsOfStudies` | Your Director of Studies | `Prof. Jane Doe` |
| `\Supervisors` | All supervisors | `Dr. A. Smith, Dr. B. Jones` |
| `\ThesisWordCount` | Approximate word count | `79,500` |

**Optional fields (uncomment to use):**

- `\dept{...}` — Department name shown on the title page.
- `\crest{...}` — University crest. The SHU crest (`SHU_crest.jpg`) is already included; uncomment the line to display it.

> **Rule:** Edit *only* `config/thesis-info.tex` and `config/ethics-approvals.tex` for all personal/administrative details. Do not hardcode your name or title anywhere else.

---

### Step 2 — Add your ethics approvals

Open **`config/ethics-approvals.tex`**. Each row of the ethics approvals table is one line in this file.

**Format:**
```latex
Ethics Review ID & Title of Study & Approval Date \\ \hline%
```

**Important rules:**
- All rows except the **last** must end with `\\ \hline%`
- The **last row** must end with just `%` (no `\\`)
- Do **not** add blank lines between rows

**Example with two approvals:**
```latex
ER20241001 & Assessment of Participant Stress Responses & 01/10/2024 \\ \hline%
ER20241002 & Follow-up Longitudinal Study & 15/11/2024%
```

**Example with one approval:**
```latex
ER20241001 & Assessment of Participant Stress Responses & 01/10/2024%
```

The table is automatically inserted into the Declaration page — you do not need to touch `frontmatter/declaration.tex`.

---

### Step 3 — Write your front matter

Edit each file in the **`frontmatter/`** folder:

| File | Contents |
|---|---|
| `frontmatter/abstract.tex` | Your thesis abstract. SHU recommends up to 300 words. |
| `frontmatter/acknowledgements.tex` | Thanks to supervisors, funders, colleagues, family. |
| `frontmatter/publications.tex` | Journal articles, conference papers, etc. arising from this thesis. Delete this section if not applicable. |
| `frontmatter/quote.tex` | An optional opening epigraph/quote. Leave blank or comment out `\input{frontmatter/quote}` in `thesis.tex` to omit. |
| `frontmatter/declaration.tex` | **Do not edit.** Auto-populated from `thesis-info.tex` and `ethics-approvals.tex`. |

---

### Step 4 — Write your chapters

1. Create a new `.tex` file inside the **`chapters/`** folder, e.g. `chapters/chapter1.tex`.
2. Begin the file with `\chapter{Your Chapter Title}`.
3. In **`thesis.tex`**, find the chapters section and add:
   ```latex
   \include{chapters/chapter1}
   ```
4. Repeat for each chapter. Keep one file per chapter for easier navigation.

**Chapter file template:**
```latex
\chapter{Introduction}
\label{ch:introduction}

\section{Background and Motivation}
Your text here.

\section{Research Aims and Objectives}
Your text here.

\section{Thesis Structure}
Your text here.
```

---

### Step 5 — Add appendices

1. Create `.tex` files inside the **`appendices/`** folder, e.g. `appendices/appendixA.tex`.
2. Begin each file with `\chapter{Appendix Title}`.
3. In **`thesis.tex`**, the appendices block uses `\appendix` to switch numbering. Add your files there:
   ```latex
   \appendix
   \include{appendices/appendixA}
   ```

---

### Step 6 — Manage your bibliography

1. Add all your references to **`bib/bibliography.bib`** in BibTeX format.
2. The template uses `natbib` by default. In-text citations use `\citep{key}` or `\citet{key}`.
3. To change the citation style, edit the `\bibliographystyle{...}` command in `thesis.tex`.

**Exporting from reference managers:**
- **Zotero / Mendeley / EndNote:** Export your library as BibTeX (`.bib`) and replace the contents of `bib/bibliography.bib`.
- **Google Scholar:** Click *Cite* → *BibTeX* and paste into the `.bib` file.

---

## AI Disclosure (Optional)

If you used AI tools (e.g. ChatGPT, GitHub Copilot, Grammarly) in preparing your thesis, SHU requires you to declare this. The template includes an optional AI disclosure statement controlled by a single toggle.

**To enable the AI disclosure:**

1. Open `config/thesis-info.tex`.
2. Change `\AIDisclosurefalse` to `\AIDisclosuretrue`.
3. Fill in the three AI fields:

```latex
\newcommand{\AITSLevel}{AITS 2 (AI for Shaping)}   % Your AITS level
\newcommand{\AIToolsUsed}{ChatGPT (openai.com)}       % Tool name and URL
\newcommand{\AIDisclosureText}{I used AI to assist with proofreading and literature summarisation.}
```

The disclosure statement will appear automatically in the Declaration. If `\AIDisclosurefalse` is set, the section is completely omitted — no further changes needed.

> Refer to the SHU AI Transparency Scale (AITS) guidance from the Research Office to determine your correct AITS level.

---

## Compiling the Thesis

### On Overleaf

1. Ensure **`thesis.tex`** is set as the main document (right-click it in the file tree → *Set as Main File*).
2. Click **Recompile** (or press `Ctrl+Enter`).
3. Overleaf uses `pdflatex` by default. The `.cls` file is already configured for this.

### Locally

Run the following sequence from the project root:

```bash
pdflatex thesis
bibtex thesis
pdflatex thesis
pdflatex thesis
```

Three `pdflatex` passes are needed to resolve cross-references, table of contents, and bibliography links correctly.

---

## Files You Should NOT Edit

| File | Reason |
|---|---|
| `thesis.tex` | Structural backbone — only add `\include` lines for new chapters/appendices |
| `PhDThesisPSnPDF.cls` | The thesis class. Editing will break formatting. |
| `frontmatter/declaration.tex` | Auto-generated from your config files. |
| `config/preamble.tex` | Only edit if you need to add advanced LaTeX packages. |

---

## SHU Submission Checklist

Before submitting your thesis, verify the following in the compiled PDF:

- [ ] Title page shows your full name, thesis title, degree, and submission date correctly
- [ ] Declaration is signed and dated
- [ ] Ethics approvals table lists all approved studies with correct reference numbers and dates
- [ ] Abstract is within the recommended word limit
- [ ] All chapters are included and page numbers are correct
- [ ] Table of Contents, List of Figures, and List of Tables are accurate
- [ ] Bibliography contains all cited works in the correct format
- [ ] Word count on the declaration matches your actual count
- [ ] AI disclosure is present (if applicable) and matches your AITS level
- [ ] The PDF compiles without errors (check the Overleaf log for warnings)

Consult the **SHU Research Degrees Regulations** and your supervisory team for the latest submission requirements.

---

## Troubleshooting

**Compilation fails on first run**
Ensure `thesis.tex` is set as the main file in Overleaf (right-click → *Set as Main File*).

**Title page shows placeholder text ("Your Thesis Title Here")**
You have not yet edited `config/thesis-info.tex`. Open it and replace all placeholder values.

**Ethics table shows a blank row at the bottom**
Check that the last row in `config/ethics-approvals.tex` ends with `%` only (no `\\`). All other rows must end with `\\ \hline%`.

**Bibliography is missing or references show as [?]**
Run BibTeX: on Overleaf this happens automatically. Locally, run `bibtex thesis` then `pdflatex` twice more.

**The SHU crest does not appear on the title page**
Uncomment `\crest{\includegraphics[width=0.4\textwidth]{SHU_crest.jpg}}` in `config/thesis-info.tex`.

**`\AIDisclosure` command not found**
Ensure `config/thesis-info.tex` contains both `\newif\ifAIDisclosure` and either `\AIDisclosurefalse` or `\AIDisclosuretrue`.

---

## Credits

- **Template developed by:** [Raymond Mawanda](https://www.shu.ac.uk), Sheffield Hallam University.
- **Adapted from:** the PhD thesis of **Muhammad Aitsam**, available in the SHU Research Archive: [shura.shu.ac.uk/37400/](https://shura.shu.ac.uk/37400/).
- **Thesis class:** `PhDThesisPSnPDF` by Krishna Kumar (Cambridge Engineering). Available at [github.com/kks32/phd-thesis-template](https://github.com/kks32/phd-thesis-template).
- **SHU customisations:** Restructured for Sheffield Hallam University PhD submissions, incorporating SHU-specific front-matter requirements (Thesis Guidelines 2024-25), the Research Ethics declaration format, and the AI Transparency Scale (AITS) disclosure framework.
- **Template repository:** [https://github.com/SHU-SIT-Lab/PhD_Thesis_Template_SheffieldHallam](https://github.com/SHU-SIT-Lab/PhD_Thesis_Template_SheffieldHallam)
---

*For queries about SHU thesis submission requirements, contact the Research Graduate School or consult your Director of Studies.*
