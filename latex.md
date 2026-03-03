# LaTeX-generated Documents

To make LaTeX-generated documents accessible, there are three key steps:
1. [Share the source LaTeX file along with the compiled PDF files](latex:share-source),
2. [Enable the PDF tagging feature in your LaTeX source file](latex:enable-tagging), and
3. [Update the content to fully utilize accessibility features](latex:update-content).

You should complete *all* three of these steps, which are detailed below.

(latex:share-source)=
## Share the Source LaTeX File

While accessibility features can be enabled using modern LaTeX compilers,
some assistive technologies may still struggle to fully parse LaTeX-generated PDF files.
By providing the source LaTeX file, you ensure that people who cannot access the PDF file can still access the content.

When uploading a LaTeX-generated PDF file to Canvas,
make sure to also upload the source LaTeX file in the same location so that it is easy to find.

:::{caution}
Before sharing the LaTeX source file, check if it contains information that is not printed in the final PDF file.
Remove any such information if you do not want it shared. For example, you may want to remove comments or hidden answers if the file is an exam or quiz.
:::

(latex:enable-tagging)=
## Enable the PDF Tagging Feature

:::{important}
You need a LaTeX distribution of **2025 or newer** to enable PDF tagging (2026 is recommended).
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

Adding this command will automatically enable tagging and accessibility compatibility features in the generated PDF.
The resulting PDF file will look visually identical, whether on screen or printed; the accessibility features are embedded behind the scenes.

If your document contains images or tables, you need to take additional steps to ensure full accessibility compliance (see [the section below](latex:update-content)).
You should also use semantic markup in your LaTeX source file (such as `\section{}` for section headings) to ensure the generated PDF file is properly tagged.

While this setup will help the resulting PDF file pass accessibility checkers, you should still include the LaTeX source file along with the PDF file when sharing on Canvas.

For equations, the setup above adds the LaTeX source code as alternative text (alt text) to math content, but this is not the best practice for people using screen readers.
See [](latex:mathml) for a better approach for math content.

### Use Packages that Support the Tagging Feature

Some LaTeX packages do not fully support PDF tagging.
If a package you are using is incompatible, the compiler may throw an error after you add the `\DocumentMetadata` options.
In such cases, first try [updating your LaTeX packages](latex:update-packages), as newer versions may have added support for PDF tagging.
If updating the packages does not solve the issue, you will need to replace the incompatible packages with compatible alternatives.

You can check the [Tagging Status of LaTeX Packages and Classes](https://latex3.github.io/tagging-project/tagging-status/#packages)
to find out whether a package is compatible with PDF tagging.
For incompatible packages, the page may also suggest compatible alternatives.

Some commonly used packages that are not fully compatible, along with their alternatives, are listed below (this list will continue to be expanded):

| Incompatible packages | Possible alternatives |
|-----------------------|-----------------------|
| `enumitem`, `exam`    | [`enumext`](https://ctan.org/pkg/enumext)   |
| `beamer`              | [`ltx-talk`](https://ctan.org/pkg/ltx-talk) |


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
