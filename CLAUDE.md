# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a LaTeX resume repository for Tony Yiding Tian containing multiple resume variants optimized for different job applications. The repository uses a custom LaTeX template based on Jake Gutierrez's resume format.

## Resume Variants

The repository contains 4 distinct resume versions:

- `resume_swe.tex` - Software Engineering focused resume (currently modified in working tree)
- `resume_cg.tex` - Computer Graphics focused resume
- `resume_hwe.tex` - Hardware Engineering focused resume
- `resume_all.tex` - Comprehensive resume with all experiences

Each resume shares the same LaTeX template structure but emphasizes different projects, skills, and experiences. All resumes except `resume_all.tex` must be controlled to 1 page length in rendered pdf.

## Building PDFs

To compile a LaTeX file to PDF, use:

```bash
pdflatex resume_swe.tex
```

This generates:
- `resume_swe.pdf` (main output)
- `resume_swe.aux` (auxiliary)
- `resume_swe.log` (compilation log)
- `resume_swe.out` (hyperref output)
- `resume_swe.synctex.gz` (SyncTeX data)

To clean up auxiliary files after compilation:

```bash
rm *.aux *.log *.out *.synctex.gz
```

## LaTeX Template Structure

All resumes follow this structure:

1. **Preamble** (lines 1-103): Document class, packages, custom commands
   - Uses `letterpaper,11pt` article class
   - Key packages: hyperref, enumitem, titlesec
   - Custom commands: `\resumeItem`, `\resumeSubheading`, `\resumeProjectHeading`

2. **Heading** (lines 110-121): Name and contact information

3. **Education** section: Uses `\resumeSubheading` command

4. **Experience** section: Professional work experience entries

5. **Projects** section: Uses `\resumeProjectHeading` for project entries

6. **Technical Skills** section: Categorized skills list

## Custom LaTeX Commands

When editing resume content, use these predefined commands:

- `\resumeSubheading{Title}{Location}{Subtitle}{Date}` - For education/experience entries
- `\resumeProjectHeading{Title}{Date}` - For project titles
- `\resumeItem{Description}` - For bullet points within sections
- `\resumeItemListStart` / `\resumeItemListEnd` - Wrap around bullet point lists

## Important Editing Guidelines

1. **ATS Compliance**: The template uses `\pdfgentounicode=1` to ensure PDFs are machine-readable by Applicant Tracking Systems

2. **Spacing**: Vertical spacing is carefully tuned. Avoid modifying `\vspace` commands unless necessary

3. **Hyperlinks**: Use `\href{url}{\underline{text}}` for clickable links (email, GitHub, project links)

4. **Special Characters**: Use LaTeX escaping: `\$` for dollar signs, `\%` for percentages, `\_` for underscores

5. **Line Length**: Keep descriptions concise to prevent page overflow. Use `\enlargethispage{20pt}` if minor overflow occurs

## Content Patterns

When adding new entries:

- **Projects**: Include technologies in italics after project name: `{\textbf{Project Name} $|$ \emph{Tech1, Tech2}}`
- **Experience**: List company/organization, role, location, and dates using `\resumeSubheading`
- **Metrics**: Include quantitative achievements (percentages, counts, performance improvements)
- **Links**: Embed GitHub repos and demo links using `\href` or `\url`

## Version Control

The repository tracks all resume variants in git. When making changes:

1. Edit the appropriate `.tex` file
2. Compile to verify PDF output
3. Commit both `.tex` and `.pdf` files if the PDF should be version-controlled

Currently modified files (per git status):
- `resume_swe.pdf`
- `resume_swe.tex`
