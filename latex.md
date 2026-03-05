# LaTeX Documents

To make LaTeX-generated documents accessible, there are three key steps:
1. [Share the source LaTeX file along with the compiled PDF files](latex:share-source),
2. [Enable the PDF tagging feature in your LaTeX source file](latex:enable-tagging), and
3. [Update the content to fully utilize accessibility features](latex:update-content).

(latex:share-source)=
## Share the Source LaTeX File

While accessibility features can be enabled using modern LaTeX compilers,
some assistive technologies may still struggle to fully parse LaTeX-generated PDF files.
The Center for Disability & Access recommends that we provide the source LaTeX file along with the PDF file to ensure that all users can access the content.

:::{caution}
Before sharing the LaTeX source file, check if it contains information that is not printed in the final PDF file.
Remove any such information if you do not want it shared. For example, you may want to remove comments or hidden answers if the file is an exam or quiz.
:::

(latex:enable-tagging)=
## Enable the PDF Tagging Feature

:::{important}
You need a LaTeX distribution from 2025 or newer to enable PDF tagging (**2026 or newer** is recommended).
See [](latex-distribution.md) for instructions.
:::

:::{tip}
Just want a TeX template to get started quickly? Check out [](latex-example.md).
:::

To enable the PDF tagging feature, add the `\DocumentMetadata` command with the appropriate options at the *very* beginning of your LaTeX source file.

```latex
\DocumentMetadata{
  lang=en-US,
  pdfversion=2.0,
  pdfstandard=ua-2,
  tagging=on,
  tagging-setup={math/alt/use}
}
```

Adding this command will automatically enable tagging and accessibility compatibility features in the generated PDF, and the resulting PDF file should pass the accessibility checker on Canvas.
The PDF file will look visually identical, whether on screen or printed; the accessibility features are embedded behind the scenes.

If your document contains images or tables, you need to take additional steps to ensure full accessibility compliance (see [the section below](latex:update-content)).
You should also use semantic markup in your LaTeX source file (such as `\section{}` for section headings) to ensure the generated PDF file is properly tagged.

For math content such as equations, the setup above adds the LaTeX source code as alternative text, but this is not the best practice for people using screen readers.
See [](latex:mathml) for a better approach for math content.

:::{tip}
If you encounter any compilation errors after adding the `\DocumentMetadata` command, please refer to the [troubleshooting guide](latex-troubleshooting) to resolve these issues.
:::

(latex:update-content)=
## Update the Content to Fully Utilize Accessibility Features

Adding `\DocumentMetadata` enables PDF tagging, but you may need to update your content to fully utilize these accessibility features.

### Add Alt Text to Images

All images in your LaTeX document should have alternative text (alt text).
You can add alt text to an image using the `alt` option in the `\includegraphics` command.
Here is an example:

```latex
\includegraphics[
  width=0.5\textwidth,
  clip,
  trim={0 1cm 0 1cm},
  alt={Repeating pattern of evenly spaced black dots arranged in staggered rows on a white background}
]{dot_pattern.png}
```

For guidance on writing good alt text, please refer to the [](images.md) page.

### Use Semantic Markup

In your LaTeX document, make sure to use semantic markup commands for various elements.
For example, use `\section{}`, `\subsection{}`, and `\paragraph{}` for headings, instead of manually changing font sizes or styles.
Similarly, use `\emph{}` for emphasis instead of changing the font to italics directly.


### Specify Header Rows in Tables

Each table should have its header row(s) specified to ensure proper tagging.
You can do this by adding the `\tagpdfsetup` command *right before* the `tabular` (or similar) environment.
Here is an example:

```latex
\tagpdfsetup{table/header-rows={1}}
\begin{tabular}{|c|c|c|}
%... table content...
```

If there are multiple header rows, specify all of them, separated by commas. For example, if the first two rows are both header rows, use:

```latex
\tagpdfsetup{table/header-rows={1,2}}
```

If there is no header row (e.g., you are using the table merely for formatting), use the following command instead:

```latex
\tagpdfsetup{table/tagging=presentation}
```

(latex:mathml)=
## Above and Beyond: Enable MathML with LuaLaTeX

While the setup above can generate PDF files that meet accessibility requirements,
you can further enhance the accessibility of math content by enabling MathML output.
To do this, you must compile your LaTeX document with `lualatex` instead of `pdflatex`.

If you have `lualatex` set up on your machine, you can enable MathML tagging with the following setup:

```latex
% !TeX program = lualatex
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
The key changes here are: (1) replacing `math/alt/use` with `math/setup=mathml-SE` in the `tagging-setup` option of `\DocumentMetadata`, (2) adding the `unicode-math` package, and (3) switching to `lualatex` for compilation (the compiler may automatically call `lualatex` when it sees the first line `% !TeX program = lualatex`, but this is not guaranteed).
:::

:::{important}
Enabling MathML makes equations more accessible, but the resulting PDF files will fail Canvas's accessibility checker.
Make sure to include the LaTeX source file along with the PDF file when sharing on Canvas.
:::

:::{seealso} Acknowledgements
This page incorporates content from the [LaTeX Tagging Project](https://latex3.github.io/tagging-project/) and feedback from [Karl Schwede](https://www.math.utah.edu/~schwede/).
:::
