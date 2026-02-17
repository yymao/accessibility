# Obtaining an Up-to-date LaTeX Distribution

To make [](latex.md) accessible, you need to have a LaTeX distribution (compiler) of 2025 or newer.
If you have an older version of LaTeX, you will encounter compiling errors when you try to include the accessible features.

:::{tip}
The version requirement is on the LaTeX compiler, not the editor.
For example, TeXmaker, TeXShop, and TeXstudio are all editors, not compilers, so their version doesn't matter.

Run `pdflatex --version` in a terminal to check the version of your LaTeX distribution.
The version number (3.14...) doesn't matter. It's the release year that matters.
:::

Below are some options for obtaining an up-to-date LaTeX distribution.

## Use Overleaf (Cloud-based Service)

If you don't want to bother with installing a new LaTeX distribution on your computer, you can consider using a cloud-based service.
The most popular one is [Overleaf](https://www.overleaf.com/). You will need to create an account to use Overleaf; a free tier is available.

By default, Overleaf uses the latest TeX Live distribution.
You can check the LaTeX compiler version by opening a project, and then going to `File` > `Settings` > `Compiler` > `TeX Live version`.
Make sure it's 2025 or newer. If it's not, you can change it to the latest version.

## Install TeX Live on a Computer

TeX Live is the most standard LaTeX distribution that can be installed on Windows, MacOS, and Linux. Here are the instructions:

- [Windows](https://tug.org/texlive/windows.html)

- [MacOS](https://tug.org/mactex/)

  There are two versions of MacTeX: the full version ([MacTeX](https://www.tug.org/mactex/mactex-download.html)) and the basic version ([BasicTeX](https://www.tug.org/mactex/morepackages.html)).
  They differ by how many features are installed and, of course, the installation size (MacTeX is about 4GB, BasicTeX is about 0.1GB).
  If you have plenty of disk space and a good Internet connection, installing the full version (MacTeX) is recommended.
  If you already have LaTeX installed on your machine, you can check whether you have MacTeX or BasicTeX installed first, then update it to the 2025 version (or newer).

- [Unix/GNU/Linux](https://www.tug.org/texlive/quickinstall.html)

  Your package manager may offer a LaTeX distribution, but it is likely to be outdated.
  Installing TeX Live from the link above will ensure that you have the latest version.
  If you already have an older version of TeX Live installed, you can also try to [upgrade it](https://www.tug.org/texlive/upgrade.html) instead of installing a new one from scratch.
