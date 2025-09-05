# LaTex template for professional project

A comprehensive LaTeX template for a professional project (thesis work format for the Systems Engineering program), designed with modern typography, proper citation handling, and code highlighting capabilities.

## Project structure

```
thesis/
├── main.tex                   # Main document file
├── preamble.tex               # Package imports and configurations
├── front_page.tex             # Title page setup
├── bibliography.bib           # Bibliography database
├── README.md                  # This documentation
├── assets/                    # Images and figures
│   └── UV.png                 # University logo
├── content/                   # Chapter files
│   ├── 01-abstract.tex
│   ├── 02-introduction.tex
│   ├── 03-problem_statement.tex
│   ├── 04-problem_justification.tex
│   ├── 05-objectives.tex
│   ├── 06-project_scope.tex
│   ├── 07-reference_framework.tex
│   ├── 08-methodology.tex
│   ├── 09-project_development_and_implementation.tex
│   └── 10-budget.tex
└── build/                     # Generated files (auto-created)
    ├── main.pdf               # Final output
    └── [auxiliary files]
```

## Quick start

### Prerequisites

#### Required packages

```bash
# Arch Linux
sudo pacman -S texlive-latex texlive-bibtexextra biber python python-pygments
```

### Compilation

### LaTex Workshop (Visual Studio Code extension)

Add the following to your `settings.json`:

```json
    "latex-workshop.latex.outDir": "./build",
    "latex-workshop.latex.tools": [
        {
            "name": "latexmk",
            "command": "latexmk",
            "args": [
                "-synctex=1",
                "-interaction=nonstopmode",
                "-file-line-error",
                "-pdf",
                "-outdir=%OUTDIR%",
                "-pdflatex=pdflatex -shell-escape %O %S",
                "%DOC%"
            ]
        }
    ]
```

## Document configuration explained

### Document class settings

```tex
\documentclass[12pt, english]{report}
```

- `12pt`: sets the base font size to $12$ points (academic standard).

- `english`: sets the document language for proper hyphenation.

- `report`: uses the report class for thesis-style documents with chapters.

### Encoding and font settings

#### Character encoding

```tex
\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
```

It ensures proper handling of special characters (accents, symbols) and enables copy-paste from PDF.

#### Modern typography

```tex
\usepackage{lmodern}
\usepackage{microtype}
```

- `lmodern`: provides high-quality scalable fonts replacing Computer Modern.

- `microtype`: improves text appearance with micro-adjustments to spacing and kerning.

### Page layout

```tex
\usepackage{geometry}
\geometry{
	left=2.54cm,
	right=2.54cm,
	top=2.54cm,
	bottom=2.54cm
}
```

Sets consistent margins ($2.54$ cm all around) following APA style guide.

### Language configuration

```tex
\usepackage[english]{babel}
```

Provides English-specific hyphenation patterns, date formatting, and language-dependent features.

### Mathematical typesetting

```tex
\usepackage{amsmath}
\usepackage{mathtools}
\usepackage{amsfonts}
\usepackage{siunitx}
```

- `amsmath`/`mathtools`: essential for complex mathematical expressions.

- `amsfonts`: provides blackboard bold, script fonts for math.

- `siunitx`: ensures consistent formatting of numbers and units (e.g., `\SI{10}{\meter}`).

### Graphics and colors

```tex
\usepackage{graphicx}
\usepackage{xcolor}
\usepackage{float}
\usepackage{caption}
```

Handles image inclusion, color definitions, and figure/table positioning and captioning.

### Hyperlinks and references

```tex
\usepackage[
	colorlinks=true,
	linkcolor=blue,
	urlcolor=blue,
	citecolor=red
]{hyperref}
\usepackage{cleveref}
```

- `hyperref`: creates clickable links in PDF (TOC, citations, references).

- `cleveref`: intelligent cross-referencing (automatically adds "Figure", "Table", etc.).

### Code and algorithms

```tex
\usepackage{algorithm}
\usepackage{algpseudocode}
\usepackage{minted}
```


- `algorithm`/`algpseudocode`: professional algorithm presentation.

- `minted`: advanced syntax highlighting using Python's Pygments (requires `--shell-escape`).

### Tables

```tex
\usepackage{tabularx}
\usepackage{booktabs}
```

creates publication-quality tables with proper spacing and rules.

### Bibliography management

```tex
\usepackage{csquotes}
\usepackage[
	backend=biber,
	style=apa,
	sorting=nyt,
	doi=true,
	url=true,
	isbn=false
]{biblatex}
```

- `csquotes`: proper quotation handling for different languages.

- `biblatex`: modern bibliography system with APA style.

- `biber`: advanced bibliography processor (successor to BibTeX).

### Custom Commands

The template includes mathematical convenience commands:

```tex
\newcommand{\norm}[1]{\left \lVert #1 \right \rVert}
\newcommand{\card}[1]{\left \lvert #1 \right \rvert}
\newcommand{\abs}[1]{\left \lvert #1 \right \rvert}

\newcommand{\ceil}[1]{\left \lceil #1 \right \rceil}
\newcommand{\floor}[1]{\left \lfloor #1 \right \rfloor}

\newcommand{\pln}[1]{\ln\left (#1 \right )}
\newcommand{\plog}[2][10]{\log_{ #1 } \left (#2 \right )}

\newcommand{\pprime}[1]{\left (#1 \right )^\prime}

\newcommand{\psin}[1]{\sin\left (#1 \right )}
\newcommand{\pcos}[1]{\cos\left (#1 \right )}
\newcommand{\ptan}[1]{\tan\left (#1 \right )}
\newcommand{\pcsc}[1]{\csc\left (#1 \right )}
\newcommand{\psec}[1]{\sec\left (#1 \right )}
\newcommand{\pcot}[1]{\cot\left (#1 \right )}

\newcommand{\parcsin}[1]{\arcsin \left (#1 \right )}
\newcommand{\parccos}[1]{\arccos \left (#1 \right )}
\newcommand{\parctan}[1]{\arctan \left (#1 \right )}
\DeclareMathOperator{\arcsec}{arcsec}
\newcommand{\parcsec}[1]{\arcsec \left (#1 \right )}
\DeclareMathOperator{\arccsc}{arccsc}
\newcommand{\parccsc}[1]{\arccsc \left (#1 \right )}
```

It provides consistent formatting for common mathematical operations.

## Document structure

### Front matter (Roman numerals)

1. Title page with university logo.

2. Table of contents.

3. List of figures.

4. List of tables.

### Main content (Arabic numerals)

1. Abstract.

2. Introduction.

3. Problem statement and justification.

4. Objectives.

5. Reference framework.

6. Project scope.

7. Methodology.

8. Development and implementation.

9. Budget.

### Back Matter

- References.

## Customization

### Adding new chapters

1. Create new `.tex` file in `content/` directory.

2. Add `\include{content/<filename>}` to `main.tex`.

### Custom title page

Modify `front_page.tex` to change title, author, or add additional information.

## Best practices

1. `Citations`: Always use `\cite{key}` for references.

2. `Figures`: Place in `assets/` directory, reference with `\includegraphics{filename}`.

3. `Cross-references`: Use `\label{}` and `\cref{}` for automatic referencing.

4. `Code blocks`: Use `minted` environment for syntax highlighting.

5. `Tables`: Use `booktabs` package for professional appearance.
