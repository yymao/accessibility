# LaTeX-generated Documents

:::{important}
You need a LaTeX distribution of **2025 or newer** to produce compliant PDF files.
:::


## The Essentials

At the *very* beginning of your LaTeX source file (even *before* setting `\documentclass`), add the following code snippet:

```latex
\DocumentMetadata{
  lang=en-US,
  pdfversion=2.0,
  pdfstandard=ua-2,
  tagging=on,
  tagging-setup={math/alt/use}
}
```

Adding the above will automatically enable tagging and accessibility compatibility features in the generated PDF.
However, there may be a few additional steps you need to take to ensure full accessibility compliance (see the sections below).

:::{tip}
Just want a template to get started? Jump to [a full working LaTeX example here](#latex-example).
:::

## Use Packages that Support the Tagging Feature

Some LaTeX packages do not fully support the PDF tagging feature.
If a package that you are using is not compatible, the compiler may throw an error after you add the `\DocumentMetadata` options.
In such cases, you will need to replace the incompatible packages with alternatives.

You can check the [Tagging Status of LaTeX Packages and Classes](https://latex3.github.io/tagging-project/tagging-status/#packages)
to find out whether a package is compatible with the PDF tagging feature.
For incompatible packages, the page may also suggest alternative packages that are compatible.

Some commonly used packages that are not fully compatible and their alternatives are listed below

| Incompatible Package | Alternative Package(s) |
|----------------------|------------------------|
| `enumitem`           | `enumext`              |


## Add Alt Text to Images

All images in the LaTeX document should have alternative text (alt text).
You can add alt text to an image by using the `alt` option in the `\includegraphics` command.
Here is an example:

```latex
\includegraphics[width=0.5\textwidth,clip,trim={0 1cm 0 1cm},alt={Repeating pattern of evenly spaced black dots arranged in staggered rows on a white background}]{dot_pattern.png}
```

For how to write good alt text, please refer to the [](images.md) page.

## Specify Header Rows in Tables

Each table should have its header row(s) specified for proper tagging.
You can do this by adding the `\tagpdfsetup` command *right before* the beginning of the `tabular` (or similar) environment.
Here is an example:

```latex
\tagpdfsetup{table/header-rows={1}}
\begin{tabular}{|c|c|c|}
%... table content...
```

If there are multiple header rows, specify all of them separated by commas. For example, if the first two rows are both header rows, do

```latex
\tagpdfsetup{table/header-rows={1,2}}
```

If there is no header row (e.g., you are using the table merely as a formatting tool), use the following command instead:

```latex
\tagpdfsetup{table/tagging=presentation}
```

## Use Semantic Markup

In your LaTeX document, make sure to use semantic markup commands for different elements.
For example, use `\section{}`, `\subsection{}`, and `\paragraph{}` for headings, instead of manually changing font sizes or styles.
Similarly, use `\emph{}` for emphasis instead of changing the font to italics directly.

## Above and Beyond: Enable MathML with LuaLaTeX

While the above setup can generate PDF files that meet the accessibility requirements,
you can further enhance the accessibility of math content by enabling MathML output.
To do this, you need to compile your LaTeX document with `lualatex` instead of `pdflatex`.

If you have `lualatex` set up on your machine, then you can enable MathML tagging with the following setup:

```latex
\DocumentMetadata{
  lang=en-US,
  pdfversion=2.0,
  pdfstandard=ua-2,
  tagging=on,
  tagging-setup={math/alt/use,math/setup=mathml-SE}
}

\documentclass{article}
\usepackage{unicode-math}
%... other packages ...
```

:::{hint}
The key changes here include adding `math/setup=mathml-SE` to the `tagging-setup` option in the `\DocumentMetadata` command, and adding the `unicode-math` package.
:::

:::{seealso}
For more comprehensive information on LaTeX accessibility, please refer to the [LaTeX Tagging Project](https://latex3.github.io/tagging-project/) page.
:::

(latex-example)=
## A Full Example of an Accessible LaTeX Document

Below is a full example of a LaTeX document that includes PDF tags and alternative text for equations.
You can use this as a template for your own LaTeX documents to ensure they are accessible.

```latex
\DocumentMetadata{
  lang=en-US,
  pdfversion=2.0,
  pdfstandard=ua-2,
  tagging=on,
  tagging-setup={math/alt/use}
}

\documentclass[11pt]{article}
\usepackage[letterpaper,margin=1in]{geometry}
\usepackage[T1]{fontenc}
\usepackage[utf8]{inputenc}
\usepackage[american]{babel}
\usepackage{graphicx}
\usepackage{hyperref}
\usepackage{enumext}
\hypersetup{pdftitle={Lecture note for Introduction Cosmology}, pdfdisplaydoctitle}

\title{Lecture note for Introduction Cosmology}
\author{Yao-Yuan Mao}
\date{February 6, 2026}
\begin{document}

\maketitle

\section*{Matter-Dominated, Flat Universe}

We begin with the Friedmann equation for a flat universe containing only (nonrelativistic) matter. There is only one term on the right-hand side:
\begin{equation}
\left( \frac{\dot a}{a} \right)^2 =
\frac{8\pi G}{3c^2}\, \frac{\epsilon_{m,0}}{a^3}.
\end{equation}

\section*{Quiz}

\begin{enumext}
  \item Consider a \emph{non-flat} universe that contains matter, radiation, \emph{and} the cosmological constant ($\Lambda$). Put the following eras in a chronological order.
  \begin{enumext}[columns=2]
     \item Curvature-dominated era
     \item Matter-dominated era
     \item Radiation-dominated era
     \item $\Lambda$-dominated era
  \end{enumext}
\end{enumext}

\end{document}
```
