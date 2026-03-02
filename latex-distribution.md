# Update LaTeX Distribution and Packages

To make [](latex.md) accessible, you need to have a LaTeX distribution (compiler) of 2025 or newer (2026 is recommended).
If you have an older version of LaTeX, you will encounter compiling errors when you try to include the accessible features.

:::{tip}
The version requirement is on the LaTeX compiler, not the editor.
For example, TeXmaker, TeXShop, and TeXstudio are all editors, not compilers, so their version doesn't matter.

Run `pdflatex --version` in a terminal to check the version of your LaTeX distribution.
The version number (3.14...) doesn't matter. It's the release year that matters.
:::

If you have confirmed that your LaTeX distribution is 2025 or newer, but you still encounter compiling errors such as "LaTeX Error: The key 'document/metadata/tagging' is unknown and is being ignored" after you add the `\DocumentMetadata` command, then you will need to update your LaTeX packages to the latest versions.

Below are some options for obtaining an up-to-date LaTeX distribution as well as instructions for updating LaTeX packages.

## Use Overleaf (Cloud-based Service)

If you don't want to bother with installing a new LaTeX distribution on your computer, you can consider using a cloud-based service.
The most popular one is [Overleaf](https://www.overleaf.com/). You will need to create an account to use Overleaf; a free tier is available.

By default, Overleaf uses the latest TeX Live distribution.
You can check the LaTeX compiler version by opening a project, and then going to `File` > `Settings` > `Compiler` > `TeX Live version`.
Make sure it is set to 2025 or newer. If it's not, you can change it to the latest version.

## Install TeX Live on a Computer

TeX Live is a standard LaTeX distribution that can be installed on Windows, macOS, and Linux. Here are the instructions:

- [Windows](https://tug.org/texlive/windows.html)

- [macOS](https://tug.org/mactex/)

  There are two versions of MacTeX: the full version ([MacTeX](https://www.tug.org/mactex/mactex-download.html)) and the basic version ([BasicTeX](https://www.tug.org/mactex/morepackages.html)).
  They differ in the number of features installed and, of course, the installation size (MacTeX is about 4GB, BasicTeX is about 0.1GB).
  If you have plenty of disk space and a good internet connection, installing the full version (MacTeX) is recommended.
  If you already have LaTeX installed on your machine, you can check whether you have MacTeX or BasicTeX installed first, then update it to the 2026 version (or newer).

- [Unix/GNU/Linux](https://www.tug.org/texlive/quickinstall.html)

  Your package manager may offer a LaTeX distribution, but it is likely to be outdated.
  Installing TeX Live from the link above will ensure that you have the latest version.
  If you already have an older version of TeX Live installed, you can also try to [upgrade it](https://www.tug.org/texlive/upgrade.html) instead of installing a new one from scratch.

(latex:update-packages)=
## Update LaTeX Packages (for TeX Live)

On macOS or Linux, you can update all of your LaTeX packages by running the following command in a terminal:

```bash
tlmgr update --self --all
```

:::{note}
If you have installed TeX Live in a root directory that requires administrator privileges, you may need to run the above command with `sudo` by adding `sudo` at the beginning of the above command.
:::


:::{tip}
Updating all the packages may take a while. If you are on or near campus, you can consider using the math department's mirror by running the following command before updating the packages:

```bash
tlmgr option repository https://ctan.math.utah.edu/ctan/tex-archive/systems/texlive/tlnet
```
:::

:::{warning}
Instructions for Windows will be coming soon.
:::