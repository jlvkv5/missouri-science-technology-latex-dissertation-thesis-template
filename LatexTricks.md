# Introduction #

Although the .cls should contain almost all necessary features, some get used in the .tex

# General latex help #

http://www.public.asu.edu/~rjansen/latexdoc/ltx-2.html

# Figures #

http://en.wikibooks.org/wiki/LaTeX/Floats,_Figures_and_Captions

# referencing various labels #

http://en.wikibooks.org/wiki/LaTeX/Labels_and_Cross-referencing

```
\label{hereisalabel}
```
```
\ref{hereisalabel}
```
Specific to amsmath
```
\eqref{hereisalabel}
```
```
\pageref{hereisalabel}
```

It is good practice to place \label{fig:picture} inside the caption of a figure.

# Manually set counters #

```
set{figure}{0}
```
```
set{chapter}{0}
```
```
set{section}{0}
```
```
set{table}{0}
```
```
set{subsection}{0}
```

# Hyphenation #

http://tex.stackexchange.com/questions/5036/how-to-prevent-latex-from-hyphenating-the-entire-document


```
adding "\raggedbottom" in the preamble fixed ALL of the page formatting issues the Grad Office had with my sections.
```


## Manually specifying where to hyphenate long words ##

http://en.wikibooks.org/wiki/LaTeX/Formatting#Hyphenation

"The command \- inserts a discretionary hyphen into a word. This also becomes the only point where hyphenation is allowed in this word."

```
Thisisareally\-longwordforlatexto\-figureoutwheretobreak.
```

# Math in chapter and section headers #

If you have a section like
```
\section{The relation $T/{\cal E}$ such and such}
```
Then hyperef will complain about `removing 'math shift' on input`. To fix, provide alternate text.
```
\section{The relation \texorpdfstring{$T/{\cal E}$}{T/E} such and such}
```
# Widows and orphans #

MS&T Office of Grad Studies says ``Need to have at least 2 lines at the top and at the bottom of every page. No lone headers at bottom of page.

```
\widowpenalty=10000
\clubpenalty=10000
```

http://en.wikibooks.org/wiki/LaTeX/Page_Layout#Widows_and_orphans

# Final corrections #

If all the above isn't enough and there are some corrections which are difficult to implement, the mstthesis.cls contains an option "`nofiles`." This tells Latex not to produce new .toc and .loi files, thus enabling you to edit them by hand before producing a .pdf.

# Printing #

If printing from Adobe reader, be sure to select "Page Scaling: None" and "Comments and Forms: Document" and unselect "Auto-Rotate and Center"