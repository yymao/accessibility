# A Full Example of an Accessible LaTeX Document

Below is a full example of a LaTeX document that includes PDF tags and alternative text for equations.
You can use this as a template for your own LaTeX documents.

For more information about making LaTeX-generated PDFs accessible, please refer to [](latex.md).

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
\hypersetup{pdftitle={Lecture note for Introduction to Cosmology}, pdfdisplaydoctitle}

\title{Lecture note for Introduction to Cosmology}
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
  \item Consider a \emph{non-flat} universe that contains matter, radiation, \emph{and} the cosmological constant ($\Lambda$). Put the following eras in chronological order.
  \begin{enumext}[columns=2]
     \item Curvature-dominated era
     \item Matter-dominated era
     \item Radiation-dominated era
     \item $\Lambda$-dominated era
  \end{enumext}
\end{enumext}

% \begin{figure}[h]
% \includegraphics[width=0.5\textwidth,clip,trim={0 1cm 0 1cm},alt={Repeating pattern of evenly spaced black dots arranged in staggered rows on a white background}]{dot_pattern.png}
% \end{figure}

\end{document}
```
