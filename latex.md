# LaTeX-generated Documents

:::{seealso}
This page focuses on practical tips to make LaTeX-generated PDF documents more accessible.
For more comprehensive information on LaTeX accessibility, please refer to the [LaTeX Tagging Project](https://latex3.github.io/tagging-project/) page.
:::

## The Essentials

At the *very* beginning of your LaTeX source file (even *before* setting `\documentclass`), add the following code snippet:

```latex
\DocumentMetadata{
  lang=en-US,
  pdfstandard=ua-2,
  pdfstandard=a-4f,
  tagging=on,
  tagging-setup={math/alt/use}
}
```

Adding the above will automatically enable tagging and accessibility compatibility features in the generated PDF.
However, there may be a few additional steps you need to take to ensure full accessibility compliance (see the sections below).

:::{note}
If your LaTeX compiler does not support `\DocumentMetadata`, you will need to update your LaTeX distribution to a more recent version.
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
  pdfstandard=ua-2,
  pdfstandard=a-4f,
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
