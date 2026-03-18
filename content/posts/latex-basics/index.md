---
title: "LaTeX: A Beginner's Guide to Document Typesetting"
date: 2026-03-18T14:00:00+05:00
draft: false
tags: ["latex", "writing", "documents", "tutorial", "beginners"]
---

## Introduction

LaTeX (pronounced *"lah-tech"* or *"lay-tech"*) is a document preparation system used widely in academia, science, and engineering. Unlike Word where you format as you type, LaTeX separates **content** from **design** — you write plain text with commands, and LaTeX handles the formatting.

It is the standard tool for writing research papers, theses, scientific articles, and mathematical documents.

---

## Why Use LaTeX?

| Feature | LaTeX | Microsoft Word |
|---|---|---|
| Math equations | Excellent | Awkward |
| Consistent formatting | Automatic | Manual |
| References & citations | Built-in | Plugins needed |
| Large documents | Handles perfectly | Can slow down |
| Output quality | Professional | Good |
| Learning curve | Steeper | Easy |

LaTeX shines when your document has **equations, citations, figures, tables, or is very long** (like a thesis).

---

## Installing LaTeX

### On Fedora/Linux

```bash
sudo dnf install texlive-scheme-full
```

Or a smaller install:

```bash
sudo dnf install texlive-scheme-basic
```

### On Ubuntu/Debian

```bash
sudo apt install texlive-full
```

### On macOS

Download **MacTeX** from [tug.org/mactex](https://tug.org/mactex)

### On Windows

Download **MiKTeX** from [miktex.org](https://miktex.org)

### Online (No Install Needed)

Use **Overleaf** at [overleaf.com](https://overleaf.com) — a free browser-based LaTeX editor. Great for beginners.

---

## Your First LaTeX Document

Create a file called `document.tex`:

```latex
\documentclass{article}

\begin{document}

Hello, World!

\end{document}
```

Compile it in the terminal:

```bash
pdflatex document.tex
```

This generates `document.pdf` — your first LaTeX document!

---

## Document Structure

Every LaTeX document follows this structure:

```latex
\documentclass{article}    % document type

% PREAMBLE — settings and packages go here
\usepackage{amsmath}        % math package
\title{My First Document}
\author{Mohsin Ali}
\date{\today}

\begin{document}            % content starts here

\maketitle                  % generate title

Your content here...

\end{document}              % content ends here
```

### Common Document Classes

| Class | Use Case |
|---|---|
| `article` | Papers, short documents |
| `report` | Longer reports with chapters |
| `book` | Books |
| `beamer` | Presentation slides |
| `letter` | Formal letters |

---

## Text Formatting

```latex
\textbf{bold text}          % bold
\textit{italic text}        % italic
\underline{underlined}      % underline
\texttt{monospace text}     % code/monospace font

\textbf{\textit{bold and italic}}   % combined
```

### Font Sizes

```latex
{\tiny tiny text}
{\small small text}
{\normalsize normal text}
{\large large text}
{\Large larger text}
{\huge huge text}
{\Huge HUGE text}
```

### Text Alignment

```latex
\begin{center}
  This text is centered.
\end{center}

\begin{flushleft}
  This text is left aligned.
\end{flushleft}

\begin{flushright}
  This text is right aligned.
\end{flushright}
```

---

## Headings and Sections

```latex
\section{Introduction}
\subsection{Background}
\subsubsection{Details}
\paragraph{A paragraph heading}
\subparagraph{A sub paragraph heading}
```

For `report` or `book` class:

```latex
\chapter{Chapter One}
\section{First Section}
```

LaTeX automatically numbers all sections for you.

---

## Lists

### Bullet List (Unordered)

```latex
\begin{itemize}
  \item First item
  \item Second item
  \item Third item
\end{itemize}
```

### Numbered List (Ordered)

```latex
\begin{enumerate}
  \item First step
  \item Second step
  \item Third step
\end{enumerate}
```

### Description List

```latex
\begin{description}
  \item[Linux] An open-source operating system
  \item[LaTeX] A document typesetting system
  \item[Git] A version control system
\end{description}
```

### Nested Lists

```latex
\begin{itemize}
  \item First item
    \begin{itemize}
      \item Nested item one
      \item Nested item two
    \end{itemize}
  \item Second item
\end{itemize}
```

---

## Math — Where LaTeX Really Shines

This is the biggest reason people use LaTeX.

### Inline Math

Use `$...$` for math inside a sentence:

```latex
The equation $E = mc^2$ changed physics forever.
```

### Display Math (Centered on Its Own Line)

Use `\[...\]` or the `equation` environment:

```latex
\[
  E = mc^2
\]

\begin{equation}
  a^2 + b^2 = c^2
\end{equation}
```

### Common Math Symbols

```latex
% Superscript and subscript
x^2          % x squared
x_i          % x sub i
x^{n+1}      % x to the power n+1
x_{ij}       % x sub ij

% Fractions
\frac{1}{2}          % 1/2
\frac{x+1}{x-1}      % (x+1)/(x-1)

% Square root
\sqrt{x}             % square root of x
\sqrt[3]{x}          % cube root of x

% Greek letters
\alpha \beta \gamma \delta
\pi \sigma \omega \theta

% Operators
\sum_{i=1}^{n} x_i        % summation
\int_0^\infty f(x)\,dx    % integral
\lim_{x \to 0} f(x)       % limit
\prod_{i=1}^{n} x_i       % product

% Arrows
\rightarrow   \leftarrow   \Rightarrow   \Leftrightarrow

% Comparison
\leq   \geq   \neq   \approx   \equiv
```

### Example — Full Equation

```latex
\begin{equation}
  \int_{-\infty}^{\infty} e^{-x^2} \, dx = \sqrt{\pi}
\end{equation}
```

### Aligned Equations

```latex
\usepackage{amsmath}   % add this in preamble

\begin{align}
  2x + 3 &= 7 \\
  2x     &= 4 \\
  x      &= 2
\end{align}
```

The `&` aligns equations at that point, `\\` starts a new line.

---

## Tables

```latex
\begin{table}[h]
  \centering
  \caption{My First Table}
  \begin{tabular}{|l|c|r|}
    \hline
    Left & Center & Right \\
    \hline
    Apple  & 5  & \$1.00 \\
    Banana & 12 & \$0.50 \\
    Orange & 8  & \$0.75 \\
    \hline
  \end{tabular}
\end{table}
```

### Column Alignment Options

| Symbol | Meaning |
|---|---|
| `l` | Left aligned |
| `c` | Center aligned |
| `r` | Right aligned |
| `\|` | Vertical line |
| `p{3cm}` | Fixed width column |

---

## Figures and Images

```latex
\usepackage{graphicx}   % add in preamble

\begin{figure}[h]
  \centering
  \includegraphics[width=0.8\textwidth]{image.png}
  \caption{This is my image}
  \label{fig:myimage}
\end{figure}
```

### Placement Options

| Option | Meaning |
|---|---|
| `h` | Here (approximately) |
| `t` | Top of page |
| `b` | Bottom of page |
| `p` | Separate page |
| `H` | Exactly here (requires `float` package) |

---

## References and Labels

LaTeX has a powerful cross-referencing system. Label anything and reference it anywhere.

```latex
\section{Introduction}
\label{sec:intro}

As discussed in Section \ref{sec:intro}...

\begin{equation}
  E = mc^2
  \label{eq:einstein}
\end{equation}

From Equation \ref{eq:einstein} we can see...

\begin{figure}[h]
  \includegraphics[width=0.5\textwidth]{photo.png}
  \caption{A photo}
  \label{fig:photo}
\end{figure}

Figure \ref{fig:photo} shows...
```

---

## Bibliography and Citations

### Simple Bibliography

```latex
\begin{thebibliography}{9}

\bibitem{knuth}
  Donald Knuth,
  \textit{The Art of Computer Programming},
  Addison-Wesley, 1968.

\bibitem{einstein}
  Albert Einstein,
  \textit{On the Electrodynamics of Moving Bodies},
  Annalen der Physik, 1905.

\end{thebibliography}
```

Cite in text:

```latex
As shown by Knuth \cite{knuth}, algorithms are important.
```

### Using BibTeX (Recommended)

Create a file `references.bib`:

```bibtex
@book{knuth1968,
  author    = {Donald Knuth},
  title     = {The Art of Computer Programming},
  publisher = {Addison-Wesley},
  year      = {1968}
}

@article{einstein1905,
  author  = {Albert Einstein},
  title   = {On the Electrodynamics of Moving Bodies},
  journal = {Annalen der Physik},
  year    = {1905}
}
```

In your `.tex` file:

```latex
\bibliographystyle{plain}
\bibliography{references}
```

Compile with:

```bash
pdflatex document.tex
bibtex document
pdflatex document.tex
pdflatex document.tex
```

---

## Useful Packages

Add these in the preamble with `\usepackage{}`:

| Package | What it does |
|---|---|
| `amsmath` | Advanced math environments |
| `graphicx` | Insert images |
| `geometry` | Page margins and size |
| `hyperref` | Clickable links and PDF bookmarks |
| `listings` | Code listings with syntax highlight |
| `xcolor` | Colors in text and backgrounds |
| `tabularx` | Better tables |
| `booktabs` | Professional table lines |
| `babel` | Multiple language support |
| `fontenc` | Better font encoding |

### Example Preamble with Common Packages

```latex
\documentclass[12pt, a4paper]{article}

\usepackage[utf8]{inputenc}
\usepackage[T1]{fontenc}
\usepackage{amsmath, amssymb}
\usepackage{graphicx}
\usepackage[margin=2.5cm]{geometry}
\usepackage{hyperref}
\usepackage{xcolor}

\title{My Research Paper}
\author{Mohsin Ali}
\date{\today}
```

---

## Page Layout

```latex
\usepackage[
  top=2.5cm,
  bottom=2.5cm,
  left=3cm,
  right=3cm
]{geometry}
```

### Two Column Layout

```latex
\documentclass[twocolumn]{article}
```

### Line Spacing

```latex
\usepackage{setspace}

\singlespacing
\onehalfspacing
\doublespacing
```

---

## Code Listings

```latex
\usepackage{listings}
\usepackage{xcolor}

\lstset{
  language=Python,
  basicstyle=\ttfamily\small,
  keywordstyle=\color{blue},
  commentstyle=\color{green},
  frame=single
}

\begin{lstlisting}
def greet(name):
    print(f"Hello, {name}!")

greet("Mohsin")
\end{lstlisting}
```

---

## Comments in LaTeX

```latex
% This is a single line comment

% LaTeX does not have multi-line comments natively
% but you can use the verbatim package or just
% comment each line individually
```

---

## Special Characters

Some characters have special meaning in LaTeX and must be escaped:

| Character | LaTeX Command |
|---|---|
| `%` | `\%` |
| `$` | `\$` |
| `&` | `\&` |
| `#` | `\#` |
| `_` | `\_` |
| `{` | `\{` |
| `}` | `\}` |
| `~` | `\textasciitilde` |
| `^` | `\textasciicircum` |
| `\` | `\textbackslash` |

---

## Compiling Your Document

```bash
pdflatex document.tex        # standard compile
xelatex document.tex         # better font support
lualatex document.tex        # most modern engine
```

For documents with bibliography:

```bash
pdflatex document.tex
bibtex document
pdflatex document.tex
pdflatex document.tex
```

You need to compile **twice** after changes so LaTeX can resolve all references and labels correctly.

---

## Quick Reference Cheat Sheet

```latex
% Document setup
\documentclass{article}
\usepackage{amsmath}
\begin{document}
\end{document}

% Text
\textbf{bold}   \textit{italic}   \underline{underline}

% Sections
\section{}  \subsection{}  \subsubsection{}

% Lists
\begin{itemize} \item ... \end{itemize}
\begin{enumerate} \item ... \end{enumerate}

% Math
$inline math$
\[ display math \]
\begin{equation} numbered equation \end{equation}

% Fractions and roots
\frac{a}{b}   \sqrt{x}   x^2   x_i

% Figure
\includegraphics[width=0.8\textwidth]{file.png}

% Table
\begin{tabular}{|l|c|r|} \hline ... \end{tabular}

% References
\label{key}   \ref{key}   \cite{key}
```

---

## Conclusion

LaTeX has a learning curve, but once you get past the basics it becomes a joy to use — especially for technical and academic writing. Your documents will look professional and consistent every time without worrying about formatting.

Start with simple documents, get comfortable with math and sections, then gradually add packages as you need them. Overleaf is the easiest way to get started without installing anything locally.

The effort you put into learning LaTeX will pay off every time you write a report, paper, or thesis. 