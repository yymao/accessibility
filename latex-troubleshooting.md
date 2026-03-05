# Troubleshooting LaTeX Issues

If you encounter any compilation errors when you turn on the PDF tagging feature in LaTeX (that is, after you add the `\DocumentMetadata` command), don't panic! Here is a step-by-step troubleshooting guide to help you resolve these issues.

## Step 1: Test with the LaTeX Template Provided

Try compiling the [LaTeX template provided](latex-example), without any modifications, and see if it works on your machine.
If it does not compile successfully, most likely you need to [upgrade your LaTeX distribution](latex-distribution) to 2026 or newer.

Once you have the latest LaTeX distribution installed, see if the template compiles successfully.
Make sure that you **remove any auxiliary files** (such as .aux, .log, .out, etc.) before recompiling each time.

## Step 2: Use the Correct Compiler

If your document still doesn't compile with the latest LaTeX distribution, check your LaTeX editor settings to make sure it is using the latest compiler you installed.

You can check the first line of the log file to see if the compiler being used is indeed the newest version (2026 or above).

Also, check if your compiler is `pdftex` or `pdflatex` when you are using `math/alt/use` in `tagging-setup`. If you are using `math/setup=mathml-SE` instead, make sure your compiler is `lualatex`.

As you switch the compiler and recompile, make sure to **remove any auxiliary files** (such as .aux, .log, .out, etc.) before recompiling each time.

## Step 3: Test with Tagging Feature Turned Off

Once you can compile the template successfully, try compiling your own LaTeX document again.
**Remove any auxiliary files** (such as .aux, .log, .out, etc.) before recompiling.

If it still doesn't compile, comment out the `\DocumentMetadata` command (and its options) and try compiling again (don't forget to remove auxiliary files first!).
This step helps identify whether there are any issues in the LaTeX source file that are not related to the PDF tagging setup.

Resolve any issues, and then restore the `\DocumentMetadata` command to see if it compiles (again, don't forget to remove auxiliary files first!).

## Step 4: Update LaTeX Packages

If your document compiles successfully without the `\DocumentMetadata` command but still fails when `\DocumentMetadata` is added back,
it is likely that some of the LaTeX packages you are using are not compatible with the PDF tagging feature.

If you haven't updated your LaTeX packages recently, try updating them first (see [](latex:update-packages) for instructions). *Note that updating packages is a distinct process from updating your LaTeX distribution*.

If you are lucky, the offending packages may have been updated to solve the issue. Make sure to remove auxiliary files before recompiling.

If your LaTeX packages are already up to date, and you still encounter compilation errors, proceed to the next step to identify which package(s) is causing the issue.

## Step 5: Identify Incompatible Packages and Replace Them

Read the error message in the log file and see if the error occurs around certain LaTeX commands that are provided by a specific package.
Once you identify the offending package(s), you will need to either remove them or replace them with compatible alternatives.

You can check the [Tagging Status of LaTeX Packages and Classes](https://latex3.github.io/tagging-project/tagging-status/#packages)
to see if there are any suggested alternatives for the incompatible package(s) you are using.

Note that if a package is listed as partially-compatible or unchecked on the tagging status page, it doesn't necessarily mean that the package is not compatible with the PDF tagging feature.
You should only consider replacing a package if you have identified it as the source of the compilation error after you turn on the PDF tagging feature.

Some commonly used packages that are not fully compatible, along with their alternatives, are listed below (this list will continue to be expanded):

| Incompatible packages | Possible alternatives |
|-----------------------|-----------------------|
| `enumitem`, `exam`    | [`enumext`](https://ctan.org/pkg/enumext)   |
| `beamer`              | [`ltx-talk`](https://ctan.org/pkg/ltx-talk) |
