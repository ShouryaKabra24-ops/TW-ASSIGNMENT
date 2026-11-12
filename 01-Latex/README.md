# Introduction to LaTeX — Practical Notes and Code Examples

> Beginner-friendly documentation based on the 64-slide **“Introduction to LaTeX (Cntd..)”** lecture PDF.
>
> These notes explain the commands in simple language and provide small examples you can copy into a `.tex` file. The examples are grouped by topic so that you can quickly find the command you need.

---

## Table of Contents

1. [What is LaTeX?](#1-what-is-latex)
2. [Basic document setup](#2-basic-document-setup)
3. [Document classes](#3-document-classes)
4. [Page margins, paper size, headers and footers](#4-page-margins-paper-size-headers-and-footers)
5. [Title page and abstract](#5-title-page-and-abstract)
6. [Changing fonts, colors and heading styles](#6-changing-fonts-colors-and-heading-styles)
7. [Lists](#7-lists)
8. [Line breaks, paragraphs and page breaks](#8-line-breaks-paragraphs-and-page-breaks)
9. [Sections and numbering](#9-sections-and-numbering)
10. [Equations](#10-equations)
11. [Lengths and spacing](#11-lengths-and-spacing)
12. [Boxes and positioning](#12-boxes-and-positioning)
13. [The `trivlist` environment and custom environments](#13-the-trivlist-environment-and-custom-environments)
14. [Finding and fixing errors](#14-finding-and-fixing-errors)
15. [Creating an index with MakeIndex](#15-creating-an-index-with-makeindex)
16. [Bibliography with BibTeX](#16-bibliography-with-bibtex)
17. [Compilation tips](#17-compilation-tips)
18. [Quick reference](#18-quick-reference)

---

## 1. What is LaTeX?

LaTeX is a document preparation system. Instead of manually formatting every line, you write text with commands and LaTeX takes care of the layout.

A LaTeX source file usually has:
- a **preamble**: document class and package settings;
- a **document body**: the content that appears in the final PDF.

A minimal file:

```latex
\documentclass[12pt,a4paper]{article}

\begin{document}
Hello, LaTeX!
\end{document}
```

**Remember:** `\documentclass` and `\usepackage` commands belong in the preamble, before `\begin{document}`.

## 2. Basic document setup

### Document class and page style

```latex
\documentclass[12pt,a4paper]{article}
\pagestyle{plain}

\begin{document}
This is my document.
\end{document}
```

- `12pt` sets the base font size.
- `a4paper` selects A4 paper.
- `article` selects the article document structure.
- `\pagestyle{plain}` displays page numbers at the bottom.

### Document class options

```latex
\documentclass[11pt,letterpaper]{report}
```

This selects the `report` class, 11-point base font and US Letter paper.

### Paper size

```latex
\documentclass[a4paper]{article}

% Alternative:
% \documentclass[letterpaper]{article}
```

Common options shown in the lecture are `a4paper` and `letterpaper`.

## 3. Document classes

The document class decides the overall structure and behavior of a document.

| Class | Common use | Main feature |
|---|---|---|
| `article` | Short documents and papers | Sections; normally no chapters |
| `report` | Longer reports | Chapters and sections |
| `book` | Books and theses | Chapters, front matter and back matter |
| `beamer` | Presentations | Slides called frames |
| `letter` | Formal letters | Recipient, opening, closing and signature |
| `exam` | Tests and quizzes | Questions and multiple-choice options |

### Book class

```latex
\documentclass{book}

\begin{document}
\frontmatter
\chapter{Preface}

\mainmatter
\chapter{Introduction}
\section{Background}

\backmatter
\chapter{References}
\end{document}
```

- `\frontmatter` starts the preliminary part of a book.
- `\mainmatter` starts the main chapters.
- `\backmatter` starts the ending material.

### Beamer slides

```latex
\documentclass{beamer}

\begin{document}

\begin{frame}{Title Slide}
Welcome to my presentation!
\end{frame}

\begin{frame}{Main Points}
\begin{itemize}
    \item First item
    \item Second item
\end{itemize}
\end{frame}

\end{document}
```

A Beamer presentation is made of `frame` environments. The text in `{...}` after `\begin{frame}` is the slide title.

### Letter class

```latex
\documentclass{letter}

\signature{Jane Doe}
\address{123 Main St.\\City, Country}

\begin{document}
\begin{letter}{Recipient Name\\Company\\Address}
\opening{Dear Recipient,}

This is an example of a letter created in LaTeX.

\closing{Sincerely,}
\end{letter}
\end{document}
```

- `\address` defines the sender's address.
- `\signature` defines the signature name.
- `\opening` and `\closing` create the greeting and sign-off.

### Exam class

The `exam` class may need to be installed in your LaTeX distribution.

```latex
\documentclass{exam}

\begin{document}
\begin{questions}

\question What is 2 + 2?
\begin{choices}
    \choice 3
    \choice 4
    \choice 5
\end{choices}

\question Explain Newton's second law.

\end{questions}
\end{document}
```

- `questions` groups the questions.
- `\question` starts a question.
- `choices` groups multiple-choice answers.
- `\choice` adds an option.

## 4. Page margins, paper size, headers and footers

### Set page margins with `geometry`

Add this in the preamble:

```latex
\usepackage{geometry}
\geometry{
    left=2.5cm,
    right=2.5cm,
    top=2.5cm,
    bottom=2.5cm
}
```

This sets all four margins to 2.5 cm.

### Page styles

```latex
\pagestyle{empty}    % No page number, header or footer
\pagestyle{plain}    % Page number at the bottom
\pagestyle{headings} % Section/chapter headings in the header
```

Choose the page style you want; a later `\pagestyle` command changes the current style.

### Custom headers and footers with `fancyhdr`

Add the package in the preamble:

```latex
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{} % Clear the default header and footer

\fancyhead[L]{Left Header}
\fancyhead[C]{Center Header}
\fancyhead[R]{Right Header}

\fancyfoot[C]{Page \thepage}
```

Another example:

```latex
\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}

\fancyhead[L]{My Document Header}
\fancyhead[C]{Center Header}
\fancyhead[R]{\today}
\fancyfoot[C]{Page \thepage}
```

Position letters:
- `L` = left
- `C` = center
- `R` = right

`\thepage` prints the current page number, and `\today` prints the current date.

## 5. Title page and abstract

### Basic title

Put the title information in the preamble and `\maketitle` in the document:

```latex
\documentclass{article}

\title{An Introduction to LaTeX}
\author{Alice Example}
\date{\today}

\begin{document}
\maketitle

This is the beginning of my document.
\end{document}
```

### Customize title formatting

```latex
\title{\Huge \bfseries Custom LaTeX Title}
\author{\Large John Doe\\
\smallskip Department of Examples}
\date{August 21, 2025}

\begin{document}
\maketitle
\end{document}
```

- `\Huge` makes text very large.
- `\bfseries` makes text bold.
- `\Large` changes the font size.
- `\\` starts a new line.
- `\smallskip` adds a small vertical gap.

### Add extra information below the title

```latex
\title{Research on LaTeX Styling}
\author{Jane Author\\University of Sample}
\date{August 2025}

\begin{document}
\maketitle

\begin{center}
    \vspace{1cm}
    \textbf{Supervisor:} Dr. Smith\\
    \textbf{Course:} Advanced Typesetting
\end{center}

\end{document}
```

`\begin{center}...\end{center}` centers the additional information.

### Abstract

```latex
\begin{abstract}
This document introduces the fundamentals of LaTeX,
including document styles, classes, title pages, and
abstract formatting.
\end{abstract}
```

An abstract is a short summary of the document. In common classes such as `article`, `report` and `book`, use the `abstract` environment.

### Abstract in Beamer

In Beamer, put the abstract text inside a titled frame:

```latex
\begin{frame}{Abstract}
This presentation covers the basics of LaTeX document
structure, including title pages and abstract environments.
\end{frame}
```

## 6. Changing fonts, colors and heading styles

### Change section heading styles with `sectsty`

Add this in the preamble:

```latex
\usepackage{xcolor}
\usepackage{sectsty}

\sectionfont{\Large\bfseries\color{blue}}
\subsectionfont{\itshape\color{red}}
```

Then use normal section commands:

```latex
\begin{document}
\section{Introduction}
\subsection{Background}
\end{document}
```

- `\sectionfont` changes section heading formatting.
- `\subsectionfont` changes subsection heading formatting.
- `\color{blue}` selects blue text.
- `\itshape` makes text italic.

### System fonts with `fontspec`

```latex
\usepackage{fontspec}

\setmainfont{Georgia}
\setsansfont{Arial}
\setmonofont{Courier New}

\begin{document}
Normal text in Georgia.

\textsf{Sans serif text in Arial.}

\texttt{Monospaced text in Courier New.}
\end{document}
```

**Important:** `fontspec` requires the XeLaTeX or LuaLaTeX compiler. It does not work with the traditional pdfLaTeX compiler. The named fonts must also be available on your system.

- `\setmainfont` sets the main (serif) font.
- `\setsansfont` sets the sans-serif font.
- `\setmonofont` sets the monospaced font.
- `\textsf{...}` produces sans-serif text.
- `\texttt{...}` produces monospaced text.

### Page background color

```latex
\usepackage{xcolor}
\pagecolor{yellow!10}

\begin{document}
This page has a light yellow background.
\end{document}
```

`yellow!10` means a light tint made with 10% yellow.

## 7. Lists

### Customize bullet lists with `enumitem`

```latex
\usepackage{enumitem}
\setlist[itemize]{label=\textbullet, leftmargin=*}

\begin{document}
\begin{itemize}
    \item First item
    \item Second item
\end{itemize}
\end{document}
```

- `enumitem` provides list-formatting controls.
- `\setlist` changes list settings.
- `label=\textbullet` sets the bullet symbol.
- `leftmargin=*` lets the list use the available left margin.

## 8. Line breaks, paragraphs and page breaks

### Manual line break

```latex
This is the first line.\\
This is the second line.
```

`\\` starts a new line without starting a new paragraph. Use it when a specific line break is needed, not after every sentence.

### New paragraph

Leave a blank line between paragraphs:

```latex
This is the first paragraph.

This is the second paragraph.
```

You can also use `\par`:

```latex
This is the first paragraph.\par
This is the second paragraph.
```

### Page break

```latex
This content is on the current page.

\newpage

This text starts at the top of the next page.
```

- `\newpage` starts a new page.
- `\pagebreak` requests a page break.
- `\clearpage` starts a new page and also outputs pending figures/tables (floats).

### Keep words together with `\mbox`

```latex
This is normal text.
\mbox{Do not break these words}
```

The content inside `\mbox{...}` is kept together as one unbreakable horizontal box.

### Keep paragraphs on the same page

```latex
\begin{samepage}
Paragraph 1 text.

Paragraph 2 text.
\end{samepage}
```

This asks LaTeX to keep the enclosed material on the same page where possible.

### Hyphenation and line breaking

```latex
% Suggest possible places to split a word:
hy-phen-ation

% Keep this word together:
\mbox{no-hyphenation}

% Request a line break:
\linebreak
```

Hyphens in a word can suggest where it may be split. `\mbox` prevents splitting inside its contents. `\linebreak` requests a line break.

## 9. Sections and numbering

### Section hierarchy

```latex
\section{Introduction}
\subsection{Background}
\subsubsection{Earlier Work}

\section{Methods}
```

LaTeX numbers sections automatically. A typical hierarchy looks like `1`, `1.1`, `1.1.1`, then `2`.

### Change the starting section number

```latex
\setcounter{section}{3}
\section{Next Section}
```

The counter is set to 3, so the next section is numbered 4.

### Unnumbered section

```latex
\section*{Acknowledgments}
```

The `*` suppresses the section number. This is useful for acknowledgments, prefaces and similar headings.

### Change section numbering to Roman numerals

```latex
\renewcommand{\thesection}{\Roman{section}}

\section{Introduction} % Displays Section I
\section{Methods}      % Displays Section II
```

`\Roman{section}` displays uppercase Roman numerals. (Use `\roman{section}` for lowercase Roman numerals.)

## 10. Equations

### Numbered equation

```latex
\begin{equation}
E = mc^2
\end{equation}
```

The `equation` environment centers an equation and automatically gives it a number.

### Unnumbered equation

Add `amsmath` in the preamble:

```latex
\usepackage{amsmath}
```

Then write:

```latex
\begin{equation*}
a^2 + b^2 = c^2
\end{equation*}
```

The star in `equation*` suppresses the equation number.

### Referencing an equation

```latex
\begin{equation}
E = mc^2
\label{eq:energy}
\end{equation}

We use Equation~\ref{eq:energy} in this explanation.
```

`\label` gives the equation a name, and `\ref` prints its number. Compile the document again if a reference initially appears as `??`.

## 11. Lengths and spacing

### Paragraph indentation and paragraph spacing

```latex
\setlength{\parindent}{2em} % Paragraph indentation
\setlength{\parskip}{1em}   % Space between paragraphs
```

- `\parindent` controls the indentation at the start of a paragraph.
- `\parskip` controls the vertical space between paragraphs.
- `em` is a unit relative to the current font size.

### Horizontal and vertical space

```latex
This is\hspace{1cm}spaced.

This is separated by\vspace{0.5cm}vertical space.
```

- `\hspace{1cm}` inserts horizontal space.
- `\vspace{0.5cm}` inserts vertical space.
- Lengths can use units such as `cm`, `mm`, `pt` and `em`.

## 12. Boxes and positioning

Boxes let you group, align, save or move content.

### Save and reuse a box

```latex
\newsavebox{\mybox}
\savebox{\mybox}{Some saved content}

\usebox{\mybox}
```

- `\newsavebox` declares a box.
- `\savebox` stores content in it.
- `\usebox` prints the stored content.

You can print the same saved content more than once:

```latex
\newsavebox{\mybox}
\savebox{\mybox}{This text is saved for reuse.}

\usebox{\mybox}

Some other content.

\usebox{\mybox}
```

### Paragraph box with `\parbox`

```latex
\parbox{5cm}{
    This text is wrapped inside a paragraph box.
    The width is fixed, so the text wraps automatically.
}
```

`\parbox{width}{content}` creates a fixed-width box that can contain a paragraph.

Another example:

```latex
\parbox{5cm}{
    This is a paragraph inside a box of fixed width.
    The text wraps automatically inside the box.
}
```

### Draw lines with `\rule`

```latex
\rule{3cm}{1pt} % Horizontal line: 3 cm wide, 1 pt high

\rule{1pt}{2cm} % Vertical line: 1 pt wide, 2 cm high
```

`\rule{width}{height}` draws a filled rectangle. A thin rectangle is commonly used as a line.

### Raise or lower content with `\raisebox`

```latex
Normal text

\raisebox{1ex}{Raised text}

\raisebox{-1ex}{Lowered text}
```

- Positive distance moves content upward.
- Negative distance moves content downward.
- `ex` is a unit based on the height of a lowercase x in the current font.

### Framed boxes with `\framebox`

```latex
\framebox[5cm][c]{Centered text in a box}

\framebox[5cm][l]{Left-aligned text}

\framebox[5cm][r]{Right-aligned text}
```

The general form is `\framebox[width][alignment]{content}`.

Alignment options:
- `c` = center
- `l` = left
- `r` = right

### Unframed boxes with `\makebox`

```latex
\makebox[4cm][c]{Unframed centered text}

\makebox[4cm][l]{Unframed left-aligned text}
```

`\makebox` works like `\framebox`, but does not draw a visible border.

### Combine boxes for a complex layout

```latex
\newsavebox{\mybox}

\savebox{\mybox}{
    \parbox{4cm}{
        \framebox[4cm][c]{Text inside a framed paragraph box}
    }
}

\usebox{\mybox}
```

This example puts a `\framebox` inside a `\parbox`, saves the result, and then displays it. Nesting boxes can help create reusable layouts.

## 13. The `trivlist` environment and custom environments

### Basic `trivlist`

```latex
\begin{trivlist}
    \item First item without label
    \item Second item
\end{trivlist}
```

`trivlist` creates a simple vertical list. Its items do not show normal bullet or number labels.

### Use `trivlist` for text blocks

```latex
\begin{trivlist}
    \item This text is part of an unlabeled list.
    \item You can add paragraphs or other content inside.
\end{trivlist}
```

Each `\item` starts a new item. Unlike `itemize`, no bullet is displayed.

### Create your own environment

```latex
\newenvironment{myenv}
    {\begin{trivlist}\item[]}
    {\end{trivlist}}

\begin{myenv}
This is a custom environment based on trivlist without item markers.
\end{myenv}
```

- `\newenvironment{myenv}{begin code}{end code}` defines a new environment.
- The first part runs when `myenv` begins.
- The second part runs when `myenv` ends.
- `\item[]` creates an item with an empty label.

## 14. Finding and fixing errors

LaTeX reports errors in the compilation log. The message usually includes the file name and a line number.

Example message:

```text
(myfile.tex [10] [11] (part2.tex
! Undefined control sequence.
l.249 \todzy
```

How to read it:
- `Undefined control sequence` means LaTeX found a command it does not recognize.
- `l.249` points to line 249.
- `\todzy` may be a typo. Check whether you meant a valid command such as `\today`.

### Common errors listed in the lecture

| Error message | What to check |
|---|---|
| `Bad \line or \vector argument` | Check the arguments supplied to `\line` or `\vector`. |
| `Bad math environment delimiter` | Check that math environments and delimiters are opened and closed correctly. |
| `\begin{...} ended by \end{...}` | Make sure each environment ends with the matching name. |
| `File ... not found` | Check the file name, path and whether the file exists. |
| `Environment ... undefined` | Check the environment name and whether the required package/class is loaded. |
| `Missing \begin{document}` | Check the document structure and preamble. |
| `Lonely \item` | Put `\item` inside a list environment. |
| `Option clash for package ...` | Check whether a package is loaded more than once with conflicting options. |
| `Too many columns in eqnarray/tabular` | Check the number of columns and `&` separators in each row. |

### Example: too many columns in a table

Incorrect:

```latex
\begin{tabular}{cc}
A & B & C
\end{tabular}
```

The column format `{cc}` declares two columns, but the row has three entries.

Correct:

```latex
\begin{tabular}{ccc}
A & B & C
\end{tabular}
```

The number of column entries must match the number of columns declared in the table format.

### A useful debugging strategy

1. Read the error message and locate the line number.
2. Undo recent edits or temporarily comment out the latest code.
3. Recompile frequently, instead of waiting until the whole document is complete.
4. If the problem is difficult to locate, make a small document containing only the code that causes the error.

### Overfull/underfull warnings and TeX capacity

The lecture mentions:
- `TeX capacity exceeded`
- `Overfull \hbox`
- `Underfull \vbox`

These can be related to resource limits or layout problems. Check the affected content and revise the text or layout. The lecture also suggests trying `\clearpage` where appropriate.

## 15. Creating an index with MakeIndex

An index helps readers find important terms and their page numbers.

### Step 1: Enable indexing in the preamble

```latex
\usepackage{makeidx}
\makeindex
```

### Step 2: Add index entries in the document

```latex
\begin{document}

A discussion about gnats.\index{gnats}

\printindex

\end{document}
```

- `\index{gnats}` adds an entry to the index.
- `\printindex` prints the index.

### Step 3: Compile

The lecture's sequence is:

```text
latex file
makeindex file
latex file
```

In command form, replace `file` with your actual file name (without the `.tex` extension), for example `latex notes.tex`, `makeindex notes`, then `latex notes.tex`.

### Types of index entries

The lecture introduces these forms:

```latex
\index{alpha}                 % Simple entry
\index{gnat!size}              % Subentry
\index{gnus!good|(}            % Start a page range
\index{gnus!good|)}            % End a page range
\index{bat|see{bats}}          % Cross-reference
\index{foo@Bar}                % Display Bar, sort under foo
\index{gnat|emph}              % Format the page number with emphasis
```

- `!` separates a main entry from a subentry.
- `@` separates the sorting text from the displayed text.
- `|` can apply a page-number formatting command or create a cross-reference.
- `|(` and `|)` mark the start and end of a page range.

### Special characters in index entries

The lecture notes that a double quote can be used to treat special index characters such as `!`, `|` and `@` as ordinary characters. For example:

```latex
\index{exclaim ("!)}
\index{foo@Bar}
\index{gnat|emph}
```

## 16. Bibliography with BibTeX

BibTeX manages references stored in a separate `.bib` file and formats the bibliography using a selected style.

### Add bibliography commands

In your `.tex` document:

```latex
\bibliographystyle{plain}
\bibliography{refs}
```

This tells LaTeX to use the `plain` bibliography style and read entries from `refs.bib` (write the file name without `.bib`).

### Create a `.bib` file

Create a file named `refs.bib` in the same folder as your `.tex` file:

```bibtex
@BOOK{kn:gnus,
  AUTHOR = "Donald E. Knudson",
  TITLE = "1966 World Gnus Almanac",
  PUBLISHER = {Permafrost Press},
  ADDRESS = {Novosibirsk},
  YEAR = 1966
}
```

### Cite the entry

In your `.tex` document, cite it using its key:

```latex
This book is used as a reference \cite{kn:gnus}.
```

The key is `kn:gnus`, the text between the braces immediately after `@BOOK{`.

### Common BibTeX entry types

| Entry type | Common required fields |
|---|---|
| `article` | `author`, `title`, `journal`, `year` |
| `book` | `author` or `editor`, `title`, `publisher`, `year` |
| `inproceedings` | `author`, `title`, `booktitle`, `year` |
| `techreport` | `author`, `title`, `institution`, `year` |
| `misc` | No universally required fields in the lecture's summary |

Other fields can include `volume`, `number`, `pages`, `publisher`, `journal` and `address`, depending on the entry type.

### Names, titles and reusable strings

```bibtex
author = {Doe, Jane}
```

or

```bibtex
author = {Jane Doe}
```

For multiple authors, separate names with `and`:

```bibtex
author = {Jane Doe and John Smith}
```

The lecture shows `and others` for an “et al.” author list:

```bibtex
author = {Jane Doe and others}
```

Protect capitalization in a title with extra braces:

```bibtex
title = {The {A}gon{y} of {G}nus}
```

Define a reusable journal abbreviation:

```bibtex
@string{jgg1 = "Journal of Gnats and Gnus, Series 1"}

@article{sample,
  author  = {Jane Doe},
  title   = {A Sample Article},
  journal = jgg1,
  year    = {2025}
}
```

For proceedings or book collections, the lecture also mentions the `crossref` field to avoid repeating shared information.

### BibTeX compilation sequence

The lecture's sequence is:

```text
latex → bibtex → latex → latex
```

The extra LaTeX runs update citations and bibliography references.

## 17. Compilation tips

The final lecture slides highlight these important points:

- Use `[fragile]` for Beamer frames that contain code or verbatim text:

  ```latex
  \begin{frame}[fragile]{Code Example}
  \begin{verbatim}
  int main() {
      return 0;
  }
  \end{verbatim}
  \end{frame}
  ```

- Keep `\documentclass` and `\usepackage` commands in the preamble.
- For an index, run LaTeX → MakeIndex → LaTeX.
- For a BibTeX bibliography, run LaTeX → BibTeX → LaTeX → LaTeX.
- Recompile after changing labels, references, citations or the index.

## 18. Quick reference

| Task | Command/package |
|---|---|
| Choose document type | `\documentclass{article}` |
| Set page style | `\pagestyle{plain}` |
| Set margins | `geometry` package |
| Customize headers/footers | `fancyhdr` package |
| Create title | `\title`, `\author`, `\date`, `\maketitle` |
| Create abstract | `abstract` environment |
| Change section fonts | `sectsty` package |
| Set system fonts | `fontspec` package (XeLaTeX/LuaLaTeX) |
| Set page background | `xcolor` and `\pagecolor` |
| Customize lists | `enumitem` and `\setlist` |
| New line | `\\` |
| New paragraph | Blank line or `\par` |
| New page | `\newpage` |
| Keep text together | `\mbox{...}` |
| Add section | `\section{...}` |
| Unnumbered section | `\section*{...}` |
| Numbered equation | `equation` environment |
| Unnumbered equation | `equation*` environment (`amsmath`) |
| Add horizontal/vertical space | `\hspace`, `\vspace` |
| Save/reuse content | `\newsavebox`, `\savebox`, `\usebox` |
| Paragraph box | `\parbox` |
| Draw a rule | `\rule` |
| Move content vertically | `\raisebox` |
| Framed box | `\framebox` |
| Unframed box | `\makebox` |
| Simple unlabeled list | `trivlist` |
| Define custom environment | `\newenvironment` |
| Create an index | `makeidx` package and `\makeindex` |
| Add bibliography | BibTeX, `\bibliography`, `\bibliographystyle` |
| Cite a reference | `\cite{key}` |

---

## Suggested repository structure

You can keep this README in the root of your GitHub repository:

```text
LaTeX-Documentation/
│
├── README.md
├── examples/
│   ├── basic-document.tex
│   ├── page-style.tex
│   ├── title-and-abstract.tex
│   ├── equations.tex
│   ├── boxes.tex
│   ├── index-example.tex
│   ├── references.tex
│   └── refs.bib
│
└── output/
    └── (compiled PDFs, if required)
```

## Source

These notes are based on the lecture PDF **“Introduction to LATEX (Cntd..)”**, 64 slides, by Dr. Neeta Nain, MNIT Jaipur. The explanations and examples above are reorganized into a practical reference for learning and revision.

