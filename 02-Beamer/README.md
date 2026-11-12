# Beamer Documentation — Complete Beginner-Friendly Guide

> A practical guide to creating presentation slides with **LaTeX Beamer**.
>
> This README explains the basic structure, frames, themes, lists, columns, images, tables, equations, blocks, overlays, and compilation process with small examples. It is written as a learning reference for a Technical Writing (TW) GitHub repository.

---

## Table of Contents

1. [What is Beamer?](#1-what-is-beamer)
2. [What You Need](#2-what-you-need)
3. [Your First Beamer Presentation](#3-your-first-beamer-presentation)
4. [Understanding the Beamer Structure](#4-understanding-the-beamer-structure)
5. [Title Page and Presentation Information](#5-title-page-and-presentation-information)
6. [Frames and Slide Titles](#6-frames-and-slide-titles)
7. [Lists and Bullet Points](#7-lists-and-bullet-points)
8. [Themes and Color Themes](#8-themes-and-color-themes)
9. [Changing Fonts and Colors](#9-changing-fonts-and-colors)
10. [Columns and Side-by-Side Content](#10-columns-and-side-by-side-content)
11. [Blocks and Alert Text](#11-blocks-and-alert-text)
12. [Images in Slides](#12-images-in-slides)
13. [Tables in Slides](#13-tables-in-slides)
14. [Mathematical Equations](#14-mathematical-equations)
15. [Overlays and Step-by-Step Reveals](#15-overlays-and-step-by-step-reveals)
16. [Code and Verbatim Text: fragile Frames](#16-code-and-verbatim-text-fragile-frames)
17. [Sections and Table of Contents](#17-sections-and-table-of-contents)
18. [Navigation Symbols and Slide Numbers](#18-navigation-symbols-and-slide-numbers)
19. [Creating a Bibliography](#19-creating-a-bibliography)
20. [A Complete Example Presentation](#20-a-complete-example-presentation)
21. [Compilation](#21-compilation)
22. [Common Errors and Fixes](#22-common-errors-and-fixes)
23. [Quick Reference](#23-quick-reference)

---

## 1. What is Beamer?

**Beamer** is a LaTeX document class used to create presentation slides. Instead of creating slides by dragging text boxes, you write LaTeX commands and compile the source into a PDF presentation.

Beamer provides:
- Frames (individual slides).
- Titles, subtitles, authors and dates.
- Themes and color themes.
- Bullet and numbered lists.
- Columns, blocks, tables, images and equations.
- Overlays to reveal content step by step.

A Beamer presentation is usually saved as a `.tex` file and compiled into a PDF.

## 2. What You Need

You need:
1. A LaTeX distribution, such as TeX Live or MiKTeX, or an online LaTeX editor.
2. A text editor, such as VS Code, or an online editor.
3. A PDF viewer to check the generated slides.

The Beamer class is included in many standard LaTeX installations. If LaTeX reports that `beamer.cls` is missing, install the Beamer package through your LaTeX distribution's package manager.

## 3. Your First Beamer Presentation

Create a file named `first-presentation.tex`:

```latex
\documentclass{beamer}

\title{My First Presentation}
\author{Student Name}
\institute{My College}
\date{\today}

\begin{document}

\begin{frame}
    \titlepage
\end{frame}

\begin{frame}{Introduction}
    Welcome to my first Beamer presentation!
\end{frame}

\end{document}
```

Compile the file. The output is a PDF with:
- A title slide.
- A second slide titled “Introduction”.

## 4. Understanding the Beamer Structure

A basic Beamer file has three main parts.

### A. Document class

```latex
\documentclass{beamer}
```

This tells LaTeX to create presentation slides instead of an article or report.

### B. Preamble

The preamble is everything before `\begin{document}`. It contains presentation details, packages and theme settings.

```latex
\documentclass{beamer}

\title{My Presentation}
\author{Student Name}
\date{\today}

\usetheme{Madrid}
```

### C. Document body

The body contains the frames (slides).

```latex
\begin{document}

\begin{frame}{First Slide}
    Slide content goes here.
\end{frame}

\end{document}
```

**Important:** `\documentclass` and `\usepackage` belong in the preamble. Each slide is normally written inside a `frame` environment.

## 5. Title Page and Presentation Information

Set the presentation details in the preamble:

```latex
\title{Introduction to Computer Science}
\subtitle{A Beginner-Friendly Overview}
\author{Student Name}
\institute{Department of Computer Science}
\date{\today}
```

Create the title slide:

```latex
\begin{document}

\begin{frame}
    \titlepage
\end{frame}

\end{document}
```

You can also write a title directly in a frame:

```latex
\begin{frame}{Welcome}
    Welcome to the presentation.
\end{frame}
```

Common title commands:

| Command | Purpose |
|---|---|
| `\title{...}` | Presentation title |
| `\subtitle{...}` | Subtitle |
| `\author{...}` | Presenter name |
| `\institute{...}` | College or organization |
| `\date{...}` | Presentation date |
| `\titlepage` | Displays the title information |

## 6. Frames and Slide Titles

A **frame** is the basic unit of a Beamer presentation. A frame usually creates one slide, although overlays can make it produce multiple PDF pages.

### Frame with a title

```latex
\begin{frame}{Introduction}
    This is the content of the slide.
\end{frame}
```

### Frame without a title

```latex
\begin{frame}
    This slide has no title.
\end{frame}
```

### Frame with a subtitle-like heading

```latex
\begin{frame}{Main Topic}
    \textbf{A smaller heading}

    More explanation goes here.
\end{frame}
```

Keep each slide focused on one main idea. Avoid putting too much text on a single slide.

## 7. Lists and Bullet Points

Beamer supports the usual LaTeX list environments.

### Unordered list with `itemize`

```latex
\begin{frame}{Features}
    \begin{itemize}
        \item Easy to structure slides
        \item Supports mathematical equations
        \item Provides themes and colors
    \end{itemize}
\end{frame}
```

### Numbered list with `enumerate`

```latex
\begin{frame}{Steps}
    \begin{enumerate}
        \item Write the LaTeX source.
        \item Compile the source file.
        \item Open the generated PDF.
    \end{enumerate}
\end{frame}
```

### Nested lists

```latex
\begin{frame}{Types of Software}
    \begin{itemize}
        \item System software
        \begin{itemize}
            \item Operating systems
            \item Device drivers
        \end{itemize}
        \item Application software
    \end{itemize}
\end{frame}
```

- `itemize` creates bullet points.
- `enumerate` creates numbered points.
- `\item` starts each list item.

## 8. Themes and Color Themes

Themes control the overall appearance of the presentation.

Set a theme in the preamble:

```latex
\usetheme{Madrid}
```

Other commonly available Beamer themes include:

```latex
\usetheme{default}
% \usetheme{Boadilla}
% \usetheme{CambridgeUS}
% \usetheme{Berlin}
% \usetheme{AnnArbor}
% \usetheme{Warsaw}
```

Use one `\usetheme` command at a time. The exact appearance depends on the selected theme and Beamer installation.

### Color themes

A color theme changes the presentation's color scheme:

```latex
\usecolortheme{default}
```

Other color themes commonly available include:

```latex
% \usecolortheme{seahorse}
% \usecolortheme{dolphin}
% \usecolortheme{beaver}
% \usecolortheme{rose}
```

Choose a theme and color theme that keep text readable. High contrast between text and background is important.

## 9. Changing Fonts and Colors

### Basic text formatting

```latex
\begin{frame}{Text Formatting}
    Normal text

    \textbf{Bold text}

    \textit{Italic text}

    \underline{Underlined text}

    {\Large Large text}

    {\small Small text}
\end{frame}
```

### Text colors with `xcolor`

```latex
\documentclass{beamer}
\usepackage{xcolor}

\begin{document}

\begin{frame}{Colors}
    \textcolor{red}{This text is red.}

    \textcolor{blue}{This text is blue.}

    \textcolor{green}{This text is green.}
\end{frame}

\end{document}
```

### Define a custom color

```latex
\usepackage{xcolor}

\definecolor{myblue}{RGB}{20, 80, 160}

% Use it in the document:
\textcolor{myblue}{Custom blue text}
```

The RGB values range from 0 to 255.

## 10. Columns and Side-by-Side Content

The `columns` environment places content next to each other.

```latex
\begin{frame}{Two Columns}

\begin{columns}

    \column{0.5\textwidth}
    \textbf{Left Column}
    \begin{itemize}
        \item Point one
        \item Point two
    \end{itemize}

    \column{0.5\textwidth}
    \textbf{Right Column}
    This is the content on the right.

\end{columns}

\end{frame}
```

- `columns` starts the column layout.
- `\column{...}` starts a column.
- `\textwidth` is the available text width.
- `0.5\textwidth` means half of the text width.

The column widths should fit within the slide, leaving room for any gap between them.

## 11. Blocks and Alert Text

Blocks help highlight definitions, examples and important information.

### Normal block

```latex
\begin{frame}{Important Concepts}

\begin{block}{Definition}
    LaTeX is a document preparation system.
\end{block}

\end{frame}
```

### Example block

```latex
\begin{frame}{Example}

\begin{exampleblock}{Example}
    This is an example of a Beamer block.
\end{exampleblock}

\end{frame}
```

### Alert block

```latex
\begin{frame}{Warning}

\begin{alertblock}{Important}
    Always save your source file before compiling.
\end{alertblock}

\end{frame}
```

- `block` creates a standard highlighted block.
- `exampleblock` highlights an example.
- `alertblock` emphasizes a warning or important point.

## 12. Images in Slides

To insert an image, use the `graphicx` package.

```latex
\documentclass{beamer}
\usepackage{graphicx}

\begin{document}

\begin{frame}{My Image}
    \centering
    \includegraphics[width=0.7\textwidth]{image.png}
\end{frame}

\end{document}
```

The image file should be in the same folder as the `.tex` file, or you should provide its correct relative path.

### Common image size options

```latex
\includegraphics[width=0.5\textwidth]{image.png}

\includegraphics[width=5cm]{image.png}

\includegraphics[height=4cm]{image.png}

\includegraphics[scale=0.5]{image.png}
```

- `width` controls the image width.
- `height` controls the image height.
- `scale` changes the image size by a factor.

### Image with a caption

```latex
\begin{frame}{College Logo}

\begin{figure}
    \centering
    \includegraphics[width=0.3\textwidth]{logo.png}
    \caption{College logo}
\end{figure}

\end{frame}
```

For a presentation, use images that are large enough to be seen clearly.

## 13. Tables in Slides

Use the `tabular` environment to create tables.

```latex
\begin{frame}{Student Details}

\begin{tabular}{|c|c|c|}
    \hline
    Name & Roll No. & Branch \\
    \hline
    Aman & 101 & CSE \\
    Riya & 102 & ECE \\
    Sam  & 103 & ME \\
    \hline
\end{tabular}

\end{frame}
```

Understanding the table syntax:

- `{|c|c|c|}` declares three centered columns with vertical lines.
- `&` separates cells.
- `\\` ends a row.
- `\hline` draws a horizontal line.

### Table with left, center and right alignment

```latex
\begin{tabular}{lcr}
    Name & Marks & Grade \\
    Aman & 85 & A \\
    Riya & 92 & A+ \\
\end{tabular}
```

Column alignment:
- `l` = left
- `c` = center
- `r` = right

## 14. Mathematical Equations

Beamer supports the same math environments as other LaTeX document classes.

### Inline equation

```latex
\begin{frame}{Mathematics}
    Einstein's equation is \(E = mc^2\).
\end{frame}
```

### Display equation

```latex
\begin{frame}{Equation}

\[
    a^2 + b^2 = c^2
\]

\end{frame}
```

### Numbered equation

```latex
\begin{frame}{Numbered Equation}

\begin{equation}
    E = mc^2
\end{equation}

\end{frame}
```

### Aligned equations

The `align` environment is provided by `amsmath` (often loaded by Beamer already; explicitly loading it is also common):

```latex
\begin{frame}{Aligned Equations}

\begin{align}
    x + y &= 10 \\
    x - y &= 2
\end{align}

\end{frame}
```

The `&` marks the alignment point, and `\\` separates equation lines.

## 15. Overlays and Step-by-Step Reveals

Overlays allow content to appear gradually. They are useful when explaining a process one point at a time.

### Using `\pause`

```latex
\begin{frame}{Learning Steps}

\begin{itemize}
    \item First, write the source code.
    \pause
    \item Next, compile the file.
    \pause
    \item Finally, view the PDF.
\end{itemize}

\end{frame}
```

Each `\pause` tells Beamer to reveal the following content on a later overlay.

### Using overlay specifications

```latex
\begin{frame}{Overlay Example}

\begin{itemize}
    \item<1-> First point
    \item<2-> Second point
    \item<3-> Third point
\end{itemize}

\end{frame}
```

- `<1->` means show from overlay 1 onward.
- `<2->` means show from overlay 2 onward.
- `<3->` means show from overlay 3 onward.

### Reveal text on a particular overlay

```latex
\begin{frame}{More Overlay Commands}

\only<1>{This text appears only on overlay 1.}

\only<2>{This text appears only on overlay 2.}

\uncover<3->{This text is revealed from overlay 3 onward.}

\end{frame}
```

- `\only` displays content only on the specified overlay.
- `\uncover` reserves space for content before it is revealed.
- Overlay specifications can be used with many Beamer commands.

## 16. Code and Verbatim Text: fragile Frames

A frame containing verbatim text or certain code listings should be marked `[fragile]`.

### Verbatim example

```latex
\begin{frame}[fragile]{C++ Code}

\begin{verbatim}
#include <iostream>
using namespace std;

int main() {
    cout << "Hello";
    return 0;
}
\end{verbatim}

\end{frame}
```

**Why `[fragile]`?**

The `verbatim` environment prints its content as-is. Beamer needs the `[fragile]` option to process frames containing verbatim material correctly.

The lecture material also highlights this rule: use `[fragile]` for frames with code or verbatim text.

## 17. Sections and Table of Contents

Sections organize a long presentation into topics.

```latex
\section{Introduction}

\begin{frame}{Introduction}
    This is the introduction.
\end{frame}

\section{Methods}

\begin{frame}{Methods}
    This slide explains the methods.
\end{frame}
```

### Display a table of contents

```latex
\begin{frame}{Contents}
    \tableofcontents
\end{frame}
```

### Show only the current section

```latex
\begin{frame}{Contents}
    \tableofcontents[currentsection]
\end{frame}
```

The table of contents is generated from the `\section` and `\subsection` commands.

## 18. Navigation Symbols and Slide Numbers

### Hide navigation symbols

Add this in the preamble:

```latex
\setbeamertemplate{navigation symbols}{}
```

This removes the small navigation icons normally shown by some Beamer themes.

### Show slide numbers in the footer

```latex
\setbeamertemplate{footline}[frame number]
```

This displays the current frame number in the footer.

### Show current slide and total slides

```latex
\setbeamertemplate{footline}[frame number]
```

The standard `frame number` template displays the current frame number. If you need a custom `current / total` footer, it can be defined with a custom footline template; that is beyond this basic example.

## 19. Creating a Bibliography

For a small presentation, references can be listed manually:

```latex
\begin{frame}{References}
    \begin{thebibliography}{9}

        \bibitem{lamport}
        Leslie Lamport.
        \textit{LaTeX: A Document Preparation System}.

        \bibitem{tantau}
        Till Tantau.
        The Beamer class documentation.

    \end{thebibliography}
\end{frame}
```

A citation can refer to an entry:

```latex
According to the Beamer documentation \cite{tantau}, ...
```

The bibliography entry must have a matching key, such as `tantau`.

## 20. A Complete Example Presentation

The following example combines the main concepts into one small presentation. Save it as `beamer-demo.tex`.

```latex
\documentclass{beamer}

% Presentation information
\title{Introduction to Beamer}
\subtitle{Creating Slides with LaTeX}
\author{Student Name}
\institute{Department of Computer Science}
\date{\today}

% Theme
\usetheme{Madrid}
\setbeamertemplate{navigation symbols}{}

% Packages
\usepackage{graphicx}
\usepackage{xcolor}
\usepackage{amsmath}

\begin{document}

% Title slide
\begin{frame}
    \titlepage
\end{frame}

% Contents
\begin{frame}{Contents}
    \tableofcontents
\end{frame}

\section{Introduction}

% Introduction slide
\begin{frame}{What is Beamer?}
    Beamer is a LaTeX document class for presentations.

    \begin{itemize}
        \item Slides are created using frames.
        \item Themes control the appearance.
        \item Mathematical equations are supported.
    \end{itemize}
\end{frame}

\section{Examples}

% Blocks
\begin{frame}{Important Information}
    \begin{block}{Definition}
        A frame is one unit of a Beamer presentation.
    \end{block}

    \begin{exampleblock}{Example}
        This is an example block.
    \end{exampleblock}

    \begin{alertblock}{Remember}
        Save your source file before compiling.
    \end{alertblock}
\end{frame}

% Columns
\begin{frame}{Two Columns}
    \begin{columns}
        \column{0.5\textwidth}
        \textbf{Left side}
        \begin{itemize}
            \item First point
            \item Second point
        \end{itemize}

        \column{0.5\textwidth}
        \textbf{Right side}
        This is the right column.
    \end{columns}
\end{frame}

% Equation
\begin{frame}{Equation}
    \[
        E = mc^2
    \]
\end{frame}

% Overlay
\begin{frame}{Step-by-Step Points}
    \begin{itemize}
        \item<1-> Write the code.
        \item<2-> Compile the file.
        \item<3-> View the PDF.
    \end{itemize}
\end{frame}

% Verbatim code: fragile is required
\begin{frame}[fragile]{Code Example}
\begin{verbatim}
int main() {
    return 0;
}
\end{verbatim}
\end{frame}

% Closing slide
\begin{frame}{Thank You}
    \centering
    Questions?
\end{frame}

\end{document}
```

## 21. Compilation

### Compile with a LaTeX editor

1. Open `beamer-demo.tex` in your LaTeX editor.
2. Select a LaTeX compiler such as pdfLaTeX.
3. Click **Compile** or **Build**.
4. Open the generated PDF and check each slide.

### Compile from a terminal

If a LaTeX distribution is installed and its commands are available in your terminal:

```bash
pdflatex beamer-demo.tex
```

Run the command again if the table of contents or references need updating.

If the `pdflatex` command is not recognized, the LaTeX distribution may not be installed or its executable folder may not be in the system PATH. An online LaTeX editor is another option.

## 22. Common Errors and Fixes

| Problem | Possible reason | What to do |
|---|---|---|
| `beamer.cls not found` | Beamer class is not installed | Install the Beamer package using your LaTeX distribution's package manager. |
| `File ... not found` | Image or other file path is incorrect | Check the file name, extension and folder. |
| `Undefined control sequence` | A command is misspelled or unavailable | Check the spelling and required package. |
| `\begin{frame}` ended by `\end{...}` | Environment names do not match | Check every `\begin` and `\end` pair. |
| Verbatim error in a frame | Frame is not marked fragile | Add `[fragile]` to the frame. |
| Text goes beyond slide edges | Too much content or a large object | Shorten the content or resize the object. |
| Table columns do not align | Wrong number of column declarations or `&` separators | Match the table format to the cells in each row. |
| Contents or references show `??` | More compilation passes may be needed | Compile again and check the labels/keys. |

### Good presentation practices

1. Keep one main idea on each slide.
2. Use short bullet points instead of long paragraphs.
3. Use readable font sizes.
4. Keep colors and themes consistent.
5. Use images only when they help explain the topic.
6. Compile regularly and check the PDF output.
7. Check that no text, image or table extends beyond the slide.

## 23. Quick Reference

| Purpose | Command |
|---|---|
| Select Beamer class | `\documentclass{beamer}` |
| Set title | `\title{...}` |
| Set author | `\author{...}` |
| Set institute | `\institute{...}` |
| Set date | `\date{...}` |
| Display title slide | `\titlepage` |
| Create a slide | `\begin{frame}{Title} ... \end{frame}` |
| Select a theme | `\usetheme{Madrid}` |
| Create bullets | `itemize` |
| Create numbered points | `enumerate` |
| Create columns | `columns`, `\column` |
| Highlight a definition | `block` |
| Highlight an example | `exampleblock` |
| Highlight a warning | `alertblock` |
| Insert an image | `\includegraphics` |
| Create a table | `tabular` |
| Display an equation | `\[ ... \]` or `equation` |
| Reveal content later | `\pause`, `<2->`, `\only` |
| Include verbatim code | `frame` with `[fragile]` |
| Add a section | `\section{...}` |
| Display contents | `\tableofcontents` |
| Hide navigation icons | `\setbeamertemplate{navigation symbols}{}` |
| Display frame number | `\setbeamertemplate{footline}[frame number]` |
| Compile to PDF | `pdflatex filename.tex` |

---

## Suggested GitHub Repository Structure

If this is part of your TW Learning Documentation repository, you can organize it like this:

```text
TW-Learning-Documentation/
│
├── README.md
│
├── 01-Latex/
│   └── README.md
│
├── 02-Beamer/
│   ├── README.md
│   ├── beamer-demo.tex
│   └── images/
│       └── (presentation images)
│
├── 03-Doxygen/
│   └── README.md
│
└── ...
```

## Source and Scope

This guide is a practical Beamer learning document. The accompanying LaTeX lecture material introduces Beamer as a slide-based document class, demonstrates a basic `frame` with a title and bullet list, and highlights the `[fragile]` option for frames containing code or verbatim text. The other Beamer examples in this README are additional standard usage examples to make the documentation useful as a standalone beginner reference.
