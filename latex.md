# LaTeX-generated Documents

:::{important}
You need a LaTeX distribution of **2025 or newer** to produce compliant PDF files.
See [](latex-distribution.md) for instructions.
:::

:::{tip}
Just want a TeX template to get started quickly? Here is [](latex-example.md).
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
The resulting PDF file will look the same visually, whether on screen or as a printout; the accessibility features are embedded behind the scenes.

If your document has images or tables, there may be additional steps that you need to take to ensure full accessibility compliance (see below).

For equations, the setup above adds the LaTeX source code as alternative text (alt text) to math content, which helps and will pass the accessibility checker, but it is not the best practice for people using screen readers. See [](latex:mathml) for a different approach for math content.


## Use Packages that Support the Tagging Feature

Some LaTeX packages do not fully support the PDF tagging feature.
If a package that you are using is not compatible, the compiler may throw an error after you add the `\DocumentMetadata` options.
In such cases, you will need to replace the incompatible packages with alternatives.

You can check the [Tagging Status of LaTeX Packages and Classes](https://latex3.github.io/tagging-project/tagging-status/#packages)
to find out whether a package is compatible with the PDF tagging feature.
For incompatible packages, the page may also suggest alternative packages that are compatible.

Some commonly used packages that are not fully compatible and their alternatives are listed below

| Incompatible packages | Possible alternatives |
|-----------------------|-----------------------|
| `enumitem`, `exam`    | [`enumext`](https://ctan.org/pkg/enumext)   |
| `beamer`              | [`ltx-talk`](https://ctan.org/pkg/ltx-talk) |


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

(latex:mathml)=
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
  tagging-setup={math/setup=mathml-SE}
}

\documentclass{article}
\usepackage{unicode-math}
%... other packages ...
```

:::{hint}
The key changes here are (1) replacing `math/alt/use` with `math/setup=mathml-SE` in `\DocumentMetadata`'s `tagging-setup` option, (2)adding the `unicode-math` package, and (3) switching to `lualatex` for compilation.

Note that enabling MathML output make the PDF file more accessible, but the resulting PDF files will fail Canvas' accessibility checker. We are seeking further guidance from CDA on this issue.
:::

:::{seealso}
For more comprehensive information on LaTeX accessibility, please refer to the [LaTeX Tagging Project](https://latex3.github.io/tagging-project/) page.
:::
