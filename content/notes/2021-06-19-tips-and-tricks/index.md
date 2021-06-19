---
title: Tips and Tricks
subtitle: Linux Ubuntu and LaTeX
summary: Linux Ubuntu and LaTeX Tips and Tricks
author: Harshvardhan
date: '2021-06-19'
slug: []
categories:
  - package
tags: []
---

## Linux Ubuntu

I kept on installing and uninstalling Ubuntu, until I shifted to Mac. This list will help me keep my mind clear of small tricks involving Terminal, if I move again.

1.  Use tls for battery preservation.
2.  Use gdebi for Debian based installs.
3.  Install Dropbox, R, RStudio, TeXLive and Spotify. You'll need them.

## LaTeX

-   **Bibliography and References:** Understand that in most academic writings they are different and Latex considers references as default. To add them, add following lines at the end of file, just before `\end{document}`.
```latex
    \bibliographystyle{apalike}
    \bibliography{bibfile}
```
Don't forget to add `\usepackage{natbib}` in the preamble. Note that bibfile.bib contains all bibliographies. If you can't get the BibTeX citations right, use Google Scholar.

- **Citations Generator:** Use this tool online to generate citations: https://truben.no/latex/bibtex/.

- **Some handy commands:** `\hfill, \vfill, \hskip, \vskip, \hspace, \vspace`. Just Google to know their usage. They're needed for extra spaces here and there in Latex documents.

- **Margins:** The easiest way is to add `\usepackage[margin=0.5in]{geometry}` in the preamble.

- **New Commands:** Outline format is `\newcommand{newname}{definition}`. See [this](https://www.overleaf.com/learn/latex/Commands) and [this](https://en.wikibooks.org/wiki/LaTeX/Macros#New_commands) for more details.

- **Style File:** Basically, they're instructions that can be used to redefine the preexisting values in the document. See my Github for two examples that I've created - one for homework assignments and other for IIM Indore's official presentation.

- **Inserting Images:** Use \usepackage{graphicx,graphics} in preamble. Then, add image with the following code block.

```latex
\begin{figure}
  \centering
    \includegraphics[width=5in]{example.png}
    \caption{An example of fitting \texttt{GP} model in 1-d function with seven data points.}
    \label{fig:example}
\end{figure}
```

- **Inserting Table:** Use [Table Generator](https://www.tablesgenerator.com) online. Create the schema and then fill in the content.

- **Horizontal Line:** `\hrulefill` for all non-tabular environments.

- **argmin and argmax:** Use this in preamble:
```latex
\DeclareMathOperator*{\argmax}{argmax}
\DeclareMathOperator*{\argmin}{argmin}
```
Then, `$\underset{x} \argmax f(x)$` or `$\underset{x} \argmax f(x)$`. This might not be very right according to this thread, but okay – it serves the purpose. If you find something better, tell me. 

- To place pictures exactly in a slide, use tikz package. Exact coordinates by cm:
```latex
\begin{tikzpicture}[remember picture,overlay]
%% (x coord, y coord) -> (0 cm, 6.5 cm)
  \node[anchor=south west,inner sep=0pt] at ($(current page.south west)+(0cm,6.5cm)$) {
     {picture.png}
  };
\end{tikzpicture}
```
The best part is that it also works for exact text placements.

- **Sum (Sigma): ** `$\sum_{i = 1}^{n} x_n$`

- **Integral:** `$\int_a^b f(x) \di x$`
- **Other math symbols:** [Overleaf](https://www.overleaf.com/learn/latex/List_of_Greek_letters_and_math_symbols) and [Oeis Wiki](https://oeis.org/wiki/List_of_LaTeX_mathematical_symbols).
- **Templates:** [Overleaf Gallery](https://www.overleaf.com/gallery/) is the best. Otherwise, you can find some repositories on Google. If you are searching for reports or presentations, or are an IIM Indore student looking for presentations, check my templates [here](project/2020-05-01-latex-templates/).
- **Tab:** The simple tab (horizontal space) can be worked with `\quad`.
- **Outer quotes:** Latex doesn't understand " as outer quotes. By default, you have to use ``. Here is a way out.
```latex
\usepackage [autostyle, english = american]{csquotes}
\MakeOuterQuote{"}
```
- **Drawing any symbol:** It is difficult to find the appropriate symbol every time, so use [Detexify](http://detexify.kirelabs.org/classify.html) to identify what you need.

