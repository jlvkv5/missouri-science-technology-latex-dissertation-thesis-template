# TOC indentation #

Sharon Matson says 20120222 the indentation should be increased for each chapter and section and subsection in the TOC. There is an aesthetic maximum and minimum, but no requirement. "5 spaces" (one tab) is suggested.

To make this correction, I wanted to include the following in the .tex file.
```
\usepackage{tocloft}
\setlength{\cftchapindent}{2em}

% chap for \chapter titles
% sec for \section titles
% subsec for \subsection titles
% subsubsec for \subsubsection titles
```
However, this causes conflicts with the .cls,
```
"! LaTeX Error: Command \c@lofdepth already defined." 
```
I also tried the following set of commands in the .cls which worked,
```
\renewcommand*\l@section{\vskip 6pt plus 1pt minus 1pt
                         \@dottedtocline{1}{4em}{2em}} 
\renewcommand*\l@subsection{\vskip 4pt minus 1pt
                         \@dottedtocline{2}{8em}{3em}}
```
But for chapters there is a pre-existing
```
\renewcommand*{\l@chapter}[2]{%
}
```
and I don't know how to edit that