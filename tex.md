# TEX

<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [TEX](#tex)
  - [常见错误](#常见错误)
  - [journal abbr](#journal-abbr)
  - [intall sty](#intall-sty)
  - [unit](#unit)
  - [chem](#chem)
  - [timer](#timer)
  - [TOC](#toc)
  - [template](#template)
    - [beamer](#beamer)
    - [article](#article)
    - [include](#include)
    - [documentclass](#documentclass)
  - [tikz](#tikz)
  - [font](#font)
    - [Blod](#blod)
    - [fonttype](#fonttype)
    - [fontsize](#fontsize)
  - [中文](#中文)
  - [cite](#cite)
    - [biblatex](#biblatex)
      - [autocite](#autocite)
      - [fullcite](#fullcite)
    - [footnote](#footnote)
      - [footnotetext](#footnotetext)
      - [footcite](#footcite)
      - [footcitetext](#footcitetext)
      - [footfullcite](#footfullcite)
      - [footfullcitetext](#footfullcitetext)
  - [variable](#variable)
  - [0补全](#0补全)
  - [loop](#loop)
  - [fileexist](#fileexist)
  - [html](#html)
  - [pagesize](#pagesize)
    - [首行缩进](#首行缩进)
    - [页边距](#页边距)
  - [filecontents](#filecontents)
  - [logo](#logo)
    - [method1](#method1)
    - [method2](#method2)
  - [换行](#换行)
  - [comment](#comment)
  - [date](#date)
  - [item](#item)
  - [symbol](#symbol)
    - [math](#math)
    - [overarc](#overarc)
    - [pvec](#pvec)
    - [双分数](#双分数)
    - [space](#space)
    - [braket](#braket)
    - [diff](#diff)
    - [subscript](#subscript)
    - [overline](#overline)
    - [degree](#degree)
    - [angstrom](#angstrom)
    - [arrow](#arrow)
    - [icon](#icon)
  - [highlight](#highlight)
    - [box](#box)
    - [beamer](#beamer-1)
  - [superlink](#superlink)
  - [double column](#double-column)
  - [equation](#equation)
    - [align](#align)
    - [gather](#gather)
    - [big bracket](#big-bracket)
  - [Listings](#listings)
    - [multicol](#multicol)
    - [listing内命令](#listing内命令)
  - [proof](#proof)
  - [Table](#table)
  - [figure](#figure)
    - [basic](#basic)
    - [position](#position)
    - [gif](#gif)
    - [subfigure](#subfigure)
    - [wrap figure](#wrap-figure)
    - [overpic](#overpic)
  - [软件体验](#软件体验)
    - [texpad](#texpad)
    - [SWiftlatex](#swiftlatex)
      - [localhost-local](#localhost-local)
      - [swift-google](#swift-google)
      - [`\ref{}`未定义](#ref未定义)
    - [BakoMa Tex](#bakoma-tex)
      - [win64](#win64)
      - [china](#china)
      - [无限试用](#无限试用)
      - [bug](#bug)
    - [texmacs](#texmacs)

<!-- /code_chunk_output -->

## 常见错误

```tex
\_
\&
```

## journal abbr

<https://github.com/compholio/jabbrv.git>

## intall sty

<https://zhuanlan.zhihu.com/p/113124407>

## unit

```tex
\usepackage{siunitx}
\SI{0.97}{g.cm^{-3}}
```

## chem

<https://mhchem.github.io/MathJax-mhchem/>

```tex
\usepackage[version=4]{mhchem}
```

adsorption

```tex
\ce{H2O\text{*} -> H\text{*} + OH\text{*}}
```

```tex
\usepackage[version=4]{mhchem}

\ph
\pka
```

## timer

<https://amito.me/2019/Adding-Timer-and-Logo-in-Beamer/>

```tex
\usepackage[timeinterval=60, timeduration=10]{tdclock}

\begin{frame}
    \titlepage
    \initclock
\end{frame}
\date{\today \crono}
```

## TOC

```tex
\tableofcontents
```

```tex
\addcontentsline{toc}{chapter{test}
\chapter*{test}
```

## template

### beamer

```tex
%---------------------------------------------------------------------------------------------------[Package]
\documentclass[aspectratio=169]{beamer}
\usepackage[T1]{fontenc}
% [移除导航]
\setbeamertemplate{navigation symbols}{}
% [theme]
\usetheme{Madrid}
\usecolortheme{beaver}
%---------------------------------------------------------------------------------------------------[Head]
%[titleset]
\title[] %optional
{}

\author{Feifei, Tian}

\institute[SHTU] % (optional)
{
  School of Physical Science and Technology\\
  ShanghaiTech University
}

\date[] % (optional)
{\today}

%-------------------------------------------------------------------------------------[atbeginsection]
\AtBeginSection[]
{
  \begin{frame}
    \frametitle{Table of Contents}
    \tableofcontents[
        sectionstyle=show/shaded,
        subsectionstyle=hide,
        subsubsectionstyle=hide
    ]
  \end{frame}
}
\AtBeginSubsection[]
{
  \begin{frame}
    \frametitle{Table of Contents}
    \tableofcontents[
        currentsubsection,
        sectionstyle=show/hide,
        subsectionstyle=show/shaded/hide,
        subsubsectionstyle=hide
    ]
  \end{frame}
}
\AtBeginSubsubsection[]
{
  \begin{frame}
    \frametitle{Table of Contents}
    \tableofcontents[
        currentsubsection,
        sectionstyle=hide,
        subsectionstyle=show/hide/hide,
        subsubsectionstyle=show/shaded/hide/hide
    ]
  \end{frame}
}
%-------------------------------------------------------------------------------------[begindocument]
\begin{document}

\frame{\titlepage}

\begin{frame}
  \frametitle{Table of Contents}
  \tableofcontents[subsectionstyle=show/show/hide]
\end{frame}
%-------------------------------------------------------------------------------------[section]
\section{First section}

\begin{frame}{}

\end{frame}

%---------------------------------------------------------------------------------------------------[END]
\end{document}
```

### article

```tex
%---------------------------------------------------------------------------------------------------[Package]
\documentclass[a4paper]{article}
\usepackage[T1]{fontenc}

\usepackage[cm]{fullpage}

\title{}
\author{}
\date{}
%-------------------------------------------------------------------------------------[begindocument]
\begin{document}

\maketitle

\begin{abstract}
\end{abstract}

%---------------------------------------------------------------------------------------------------[END]
\end{document}
```

### include

```tex
\input{~/codes/group/common/beamer_header}
```

### documentclass

<https://en.wikibooks.org/wiki/LaTeX/Document_Structure>
|Command                            |Level  |Comment
|---                                |---    |---
|`\part{''part''}`                  |-1     |not in letters
|`\chapter{''chapter''}`            |0      |only books and reports
|`\section{''section''}`            |1      |not in letters
|`\subsection{''subsection''}`      |2      |not in letters
|`\subsubsection{''subsubsection''}`|3      |not in letters
|`\paragraph{''paragraph''}`        |4      |not in letters
|`\subparagraph{''subparagraph''}`  |5      |not in letters

## tikz

```tex
%-------------------------------------------------------------------------------------[flowchart]
\usepackage{tikz}
\usetikzlibrary{shapes.geometric, arrows}
\tikzstyle{startstop} = [rectangle, rounded corners, minimum width=3cm, minimum height=1cm,text centered, draw=black, fill=red!30]
\tikzstyle{io} = [trapezium, trapezium left angle=70, trapezium right angle=110, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=blue!30]
\tikzstyle{process} = [rectangle, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=orange!30]
\tikzstyle{decision} = [diamond, minimum width=3cm, minimum height=1cm, text centered, draw=black, fill=green!30]
\tikzstyle{arrow} = [thick,->,>=stealth]

\definecolor{color1}{RGB}{254, 125, 106}

\begin{center}
\begin{tikzpicture}[node distance=1.5cm]
    \node (start) [startstop] {};
    \node (pro1) [process, below of=start,yshift=0cm] {};
    \node (pro2) [process, below of=pro1] {};
    \node (end) [startstop, below of=pro2] {};
    \draw [arrow,color=color1] (start) -- (pro1);
    \draw [arrow] (pro1) -- (pro2);
    \draw [arrow] (pro2) -| node[anchor=south west] {Theory} ([xshift=2cm, yshift=0cm]pro2.east) |-  (pro1);
    \draw [arrow] (pro2) -- (end);
\end{tikzpicture}
\end{center}

% https://www.overleaf.com/learn/latex/LaTeX_Graphics_using_TikZ:_A_Tutorial_for_Beginners_(Part_3)%E2%80%94Creating_Flowcharts
% https://stackoverflow.com/questions/29963701/latex-flowchart-line-crossing-line
```

## font

<https://en.wikibooks.org/wiki/LaTeX/Fonts>

### Blod

global bold

```tex
\renewcommand{\seriesdefault}{\bfdefault}
```

math bold  
<https://tex.stackexchange.com/questions/376665>

```tex
\mathversion{bold}
```

### fonttype

need XeLaTeX

```tex
\setmainfont{Arial}
```

math fonttype  
<https://tex.stackexchange.com/questions/469775/how-to-use-math-mode-and-siunitx-with-arial>

```tex
\usepackage{unicode-math}

\setmathfont{GFSNeohellenicMath.otf}
\setmathfont[range=up]{Arial}
\setmathfont[range=it]{Arial Italic}
\setmathfont[range=bfup]{Arial Bold}
\setmathfont[range=bfit]{Arial Bold Italic}
```

### fontsize

global fontsize

```tex
\documentclass[12pt]{article}
```

```tex
\renewcommand{\small}{\fontsize{12pt}{0pt}\selectfont}
```

equation \& table

```tex
\begin{small}
    \begin{table}
    \end{table}
\end{small}

\begin{table}
    \small
\end{table}

\begin{small}
    \[
    \]
\end{small}
```

print fontsize

```tex
\makeatletter
\newcommand\thefontsize{\f@size pt}
\makeatother
```

<https://tex.stackexchange.com/questions/24599/what-point-pt-font-size-are-large-etc>

## 中文

```tex
%-------------------------------------------------------------------------------------[documentclass]
\documentclass{ctexart}
%-------------------------------------------------------------------------------------[cn]
\usepackage{ctex}
% or
\usepackage{xeCJK}
%-------------------------------------------------------------------------------------[字体]
% bakama 禁用

% 加黑宋体
\setCJKmainfont{FandolSong}

% 华文新魏
\setCJKmainfont{STXinwei}

\newfontfamily\kai{STKaiti}
\kai 楷体

% https://www.kancloud.cn/digest/latexeverywhere/181885

%-------------------------------------------------------------------------------------[date]
\zhdate{2021/2/22}
%-------------------------------------------------------------------------------------[Bakoma CN]
% Immitate PDFTeX only for CTEX/expl3
\ifdefined\XeTeXversion\else\ifdefined\pdftexversion\else
        \newcount\pdftexversion\pdftexversion=140
        \def\pdftexrevision{18}
    \fi\fi
```

## cite

### biblatex

```tex
\usepackage[style=phys]{biblatex}
\addbibresource{references.bib}

\cite{}

\printbibliography
```

#### autocite

```tex
\usepackage[style=phys,autocite=plain]{biblatex}

\autocite{}
```

#### fullcite

```tex
\usepackage[style=nature]{biblatex}

\fullcite{}
```

fullcite in section 失效问题

```tex
\section{\fullcite{}}
\fullcite{}
```

### footnote

```tex
\footnote{}
```

字号

```tex
% 7pt 字号，9pt baselineskip
\renewcommand{\footnotesize}{\fontsize{7pt}{9pt}\selectfont}
```

#### footnotetext

```tex
\footnotemark
\footnotemark
\addtocounter{footnote}{-2}

\addtocounter{footnote}{1}
\footnotetext{test1}
\addtocounter{footnote}{1}
\footnotetext{test2}
```

#### footcite

```tex
\usepackage[style=nature,doi=false,url=false]{biblatex}
```

多引用,

```tex
\usepackage{fnpct}
\AdaptNote\footcite{oo+m}[footnote]{%
\setfnpct{dont-mess-around}%
\IfNoValueTF{#1}
{#NOTE{#3}}
{\IfNoValueTF{#2}{#NOTE[#1]{#3}}{#NOTE[#1][#2]{#3}}}%
}
```

#### footcitetext

```tex
\footcitetext{test1}
```

#### footfullcite

```tex
\usepackage[style=nature,doi=false,url=false]{biblatex}
```

多引用`,`

```tex
\usepackage{fnpct}
\AdaptNote\footfullcite{oo+m}[footnote]{%
\setfnpct{dont-mess-around}%
\IfNoValueTF{#1}
{#NOTE{#3}}
{\IfNoValueTF{#2}{#NOTE[#1]{#3}}{#NOTE[#1][#2]{#3}}}%
}
```

#### footfullcitetext

<https://tex.stackexchange.com/questions/420162/footfullcite-not-showing-when-used-within-a-wrapfigure>

```tex
\newcommand*\publistbasestyle{nature}
\usepackage[bibstyle=publist,linktitleall=true,isbn=false,doi=false,url=false,eprint=false,plauthorhandling=highlight,boldyear=false,nameorder=given-family]{biblatex}
\plauthorname[Feifei]{Tian}
\renewcommand{\footnotesize}{\fontsize{7pt}{9pt}\selectfont}
\DeclareCiteCommand{\footfullcitetext}[\mkbibfootnotetext]
  {\usebibmacro{prenote}}
  {\usedriver
     {\DeclareNameAlias{sortname}{default}}
     {\thefield{entrytype}}}
  {\multicitedelim}
  {\usebibmacro{postnote}}
\newrobustcmd*{\footfullcitetextallauthor}{%
  \AtNextCite{\AtEachCitekey{\defcounter{maxnames}{999}}}%
  \footfullcitetext}

\addtocounter{footnote}{1}
\footfullcitetext{test1}
```

## variable

<https://www.overleaf.com/learn/latex/Commands>

```tex
\newcommand{\x}{30}
```

```tex
\newcommand{\x}[3][1]{(#2 + #3)^#1}
\newcommand{\<name of var>}[<num of var>][<default var>]{(#2 + #3)^#1}

\[
    \x{4}{x}{y}
\]
```

## 0补全

```tex
\makeatletter
\renewcommand\theimonth{\two@digits{\value{imonth}}}    
\makeatother
```

<https://tex.stackexchange.com/questions/30930/how-to-output-a-counter-with-leading-zeros>

## loop

```tex
\newcounter{i}
\newcounter{j}

\setcounter{i}{1}
\loop
{%
    \setcounter{j}{1}
    \loop
    {%
        \thei.\thej
        \addtocounter{j}{1}
    }%
    \ifnum \value{j}<10
    \repeat
    %
    \addtocounter{i}{1}
}%
\ifnum \value{i}<10
\repeat
```

## fileexist

```tex
\IfFileExists{./filename}{true-branch}{false-branch}
```

## html

```html
<img src="https://render.githubusercontent.com/render/math?math=e^{i \pi} = -1">
```

<https://gist.github.com/a-rodin/fef3f543412d6e1ec5b6cf55bf197d7b>
<https://github.com/TeamMeow/vscode-math-to-image>

## pagesize

```tex
\usepackage[margin=0in,paperwidth=3.25in,paperheight=1.75in]{geometry}
```

### 首行缩进

```tex
\parindent 0in
```

### 页边距

```tex
\usepackage{geometry}
\geometry{a4paper,left=0cm,right=0cm,top=0cm,bottom=0cm}
```


## filecontents

强制 overwrite

```tex
\makeatletter
\let\oldfilec@ntents\filec@ntents
\gdef\filec@ntents{\filec@ntents@overwrite\oldfilec@ntents}
\makeatother

\begin{filecontents}{temp_filecontents.tex}
\end{filecontents}
```

## logo

### method1

```tex
\usepackage{tikz}
\newcommand{\mylogo}{
    \begin{tikzpicture}[remember picture,overlay]
        \node[xshift=-0.5cm,yshift=-0.5cm] at (current page.north east) {\includegraphics[width=1cm]{Shanghaitech}};
    \end{tikzpicture}
}
```

放在 frame 最后

```tex
\mylogo
```

<https://tex.stackexchange.com/questions/16357/how-can-i-position-an-image-in-an-arbitrary-position-in-beamer>

### method2

<https://amito.me/2019/Adding-Timer-and-Logo-in-Beamer/>

```tex
\setbeamertemplate{frametitle}
{\begin{beamercolorbox}[wd=\paperwidth]{frametitle}
      \strut\hspace{0.5em}\insertframetitle\strut
      \hfill
      \raisebox{-2mm}{\includegraphics[width=1cm]{$logo$}}
    \end{beamercolorbox}
}
```

## 换行

- 空行 最合理
- `\par` 等同于空行
- `\\` 对齐时使用

## comment

```tex
\usepackage{comment}

\begin{comment}
\end{comment}
```

## date

```tex
\usepackage[USenglish,UKenglish,french,spanish,italian]{babel}
\usepackage[useregional]{datetime2}


% after begindocument
\selectlanguage{USenglish}
\DTMdate{2021-5-6}
```

<https://tex.stackexchange.com/questions/141824/how-to-write-a-non-today-date-in-latex-with-localization-formatting>

## item

<https://www.overleaf.com/learn/latex/lists>

unordered

```tex
\begin{itemize}
    \item something
\end{itemize}
```

ordered

```tex
\begin{enumerate}
\end{enumerate}
```

description

```tex
\begin{description}
   \item This is an entry \textit{without} a label.
   \item[Something short] A short one-line description.
\end{description}
```

change label

```tex
\begin{itemize}
  \item This is my first point
  \item Another point I want to make 
  \item[!] A point to exclaim something!
  \item[$\blacksquare$] Make the point fair and square.
  \item[NOTE] This entry has no bullet
  \item[] A blank label?
\end{itemize}
```

<https://tex.stackexchange.com/questions/50269/itemize-without-bullets>

## symbol

### math

```tex
\usepackage{mathrsfs}
\mathscr{C}
```

### overarc

<https://tex.stackexchange.com/questions/96680/a-better-notation-to-denote-arcs-for-an-american-high-school-textbook>

```tex
\DeclareFontFamily{OMX}{yhex}{}
\DeclareFontShape{OMX}{yhex}{m}{n}{<->yhcmex10}{}
\DeclareSymbolFont{yhlargesymbols}{OMX}{yhex}{m}{n}
\DeclareMathAccent{\wideparen}{\mathord}{yhlargesymbols}{"F3}

\wideparen{AB}
```

### pvec

```tex
\newcommand{\pvec}[1]{\vec{#1}\mkern2mu\vphantom{#1}}
```

### 双分数

```tex
\newcommand{\ddfrac}[2]{\frac{\displaystyle #1}{\displaystyle #2}}
```

### space

```tex
\quad
\medskip
```

<https://tex.stackexchange.com/questions/74353/what-commands-are-there-for-horizontal-spacing>

### braket

```tex
\usepackage{braket}
\braket{d}
```

### diff

<https://tex.stackexchange.com/questions/203508/d-with-a-little-line-through-the-top-of-it>

```tex
\newcommand*{\diff}{\mathop{}\!\mathrm{d}}
\newcommand*{\dbar}{\mathop{}\!\mathrm{d}\hspace*{-0.15em}\bar{}\hspace*{0.1em}}
```

### subscript

```tex
\textsubscript
\textsuperscript
```

### overline

```tex
$\overline{2}$
\bar{2}
```

### degree

```tex
\textdegree
```

<https://tex.stackexchange.com/questions/384873/what-is-the-degree-symbol/384874>

### angstrom

```tex
\AA
```

### arrow

```tex
$
    \xleftarrow{n=0}
    \xrightarrow[T]{n>0}
$
```

<https://www.cnblogs.com/wt869054461/p/9544846.html>

### icon

```tex
\usepackage{fontawesome}

\faPhone
\faEnvelope
\faHome
\faGlobe
```

## highlight

### box

<https://texample.net/tikz/examples/boxes-with-text-and-math/>
<https://tex.stackexchange.com/questions/521148/how-can-i-get-the-definition-and-theorem-environment-like-these-in-latex-package>

```tex
\usepackage{xcolor}
\definecolor{amber}{rgb}{1.0, 0.49, 0.0}

\usepackage{tikz}

\tikzstyle{boxtitle} = [fill=amber, text=white]
\tikzstyle{boxstyle} = [draw=amber,fill=gray!17,
    thick,rectangle,rounded corners,inner sep=10pt, inner ysep=20pt]
\newcommand{\mybox}[3][\textwidth]{
    \par\noindent
    \begin{tikzpicture}
        \node [boxstyle] (box){%
            \begin{minipage}{#1}{#3}\end{minipage}
        };
        \node[boxtitle,right=10pt] at (box.north west) {#2};
    \end{tikzpicture}
}

\mybox{0.5\textwidth}{some title}{something}
```

### beamer

```tex
\begin{frame}{}

    \alert{something}

    \begin{block}{}
    \end{block}

    \begin{alertblock}{}
    \end{alertblock}

    \begin{examples}
    \end{examples}

\end{frame}
```

## superlink

```tex
% 放到 usepackage 最后
\usepackage{hyperref}

\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    filecolor=magenta,
    urlcolor=cyan,
    citecolor=black,
}
\urlstyle{same}

\href{.com}{Something}
\url{.com}
```

## double column

```tex
\begin{frame}{}

\begin{columns}
    \column{0.5\textwidth}
\end{columns}

\begin{columns}
    \begin{column}{0.5\textwidth}
    \end{column}
\end{columns}

\end{frame}
```

## equation

<https://www.overleaf.com/learn/latex/Aligning_equations_with_amsmath>

```tex
\usepackage{amsmath}
```

### align

```tex
\begin{align}
x&=y           &  w &=z              &  a&=b+c\\
2x&=-y         &  3w&=\frac{1}{2}z   &  a&=b\\
-4 + 5x&=2+y   &  w+2&=-1+w          &  ab&=cb
\end{align}
```

### gather

```tex
\begin{gather}
    \label{eq:}
\end{gather}
```

```tex
\begin{gather}
    \begin{aligned}
    \end{aligned}
\end{gather}
```

### big bracket

```tex
\begin{align}
    \left\{
    \begin{aligned}
    \end{aligned}
    \right.
\end{align}
```

## Listings

<https://www.overleaf.com/learn/latex/Code_listing>

style

```tex
\usepackage{listings}
\usepackage{xcolor}
\definecolor{codegreen}{rgb}{0,0.6,0}
\definecolor{codegray}{rgb}{0.5,0.5,0.5}
\definecolor{codepurple}{rgb}{0.58,0,0.82}
\definecolor{backcolour}{rgb}{0.95,0.95,0.92}

\lstdefinestyle{mystyle}{
    backgroundcolor=\color{backcolour},
    commentstyle=\color{codegreen},
    keywordstyle=\color{magenta},
    numberstyle=\tiny\color{codegray},
    stringstyle=\color{codepurple},
    basicstyle=\ttfamily\fontsize{9pt}{11pt}\selectfont,
    breakatwhitespace=false,
    breaklines=true,
    captionpos=b,
    keepspaces=true,
    numbers=left,
    numbersep=5pt,
    showspaces=false,
    showstringspaces=false,
    showtabs=false,
    tabsize=2
}
\lstset{style=mystyle}
```

file

```tex
\lstinputlisting[language=bash,caption=]{file}
```

code block

```tex
\begin{lstlisting}[language=bash]
\end{lstlisting}
```

inline

```tex
\lstinline{for}
```

Note in beamer

```tex
\begin{frame}[fragile]
\end{frame}
```

<https://tex.stackexchange.com/questions/130109/cant-insert-code-in-my-beamer-slide>

### multicol

```tex
\usepackage{multicol}
\lstinputlisting[multicols=4]{data.txt}
```

### listing内命令

```tex
\begin{lstlisting}[escapechar=\%]
%\leftarrow%
\end{lstlisting}
```

## proof

```tex
\usepackage{amssymb,amsthm}
```

## Table

```tex
\begin{table}[ht]
    \centering
    \begin{tabular}{c c c}
    \hline
        &   &   \\
    \hline
        &   &   \\    
    \hline
    \end{tabular}
    \caption{}
    \label{table:}
\end{table}
```

multirow

```tex
\usepackage{multirow}

\begin{table}[ht]
    \centering
    \begin{tabular}{c|cc}
    \hline
        &\multicolumn{2}{c}{} \\
    \hline
    \multirow{2}{*}{}   &   &   \\
                        &   &   \\
    \hline
    \end{tabular}
\end{table}
```

## figure

### basic

```tex
\usepackage{graphicx}

\begin{figure}[ht]
    \centering
    \includegraphics[width=0.75\textwidth,height=0.75\textheight]{Xas_Pt_O_vac/Xas_Pt_O_vac}
    \caption{}
    \label{fig:}
\end{figure}
```

### position

<https://www.overleaf.com/learn/latex/Inserting_Images>
```tex
\usepackage{float}
\begin{figure}[H]
```

### gif

```tex
\usepackage{animate}

\begin{figure}
    \animategraphics[loop,controls={play,step,speed},width=0.8\textwidth]{20}{test}{0008}{0032}
    \centering
\end{figure}
```

### subfigure

```tex
\usepackage{subcaption}
\newcommand{\subfigwid}{0.495}

\renewcommand{\subfigwid}{0.495}
\begin{figure}
    \centering
    %
    \begin{subfigure}[b]{\subfigwid\textwidth}
        \centering
        \includegraphics[height=0.8\textheight]{graph1}
        \caption{}
        \label{fig:}
    \end{subfigure}
    %
    \begin{subfigure}[b]{\subfigwid\textwidth}
        \centering
        \includegraphics[height=0.8\textheight]{graph3}
        \caption{}
        \label{fig:}
    \end{subfigure}
    %
    \caption{}
    \label{fig:}
\end{figure}
```

### wrap figure

```tex
\usepackage{wrapfig}

\begin{wrapfigure}{r}{0.25\textwidth} %this figure will be at the right
    \centering
    \includegraphics[width=0.25\textwidth]{mesh}
\end{wrapfigure}
```

### overpic

```tex
\usepackage{overpic}
\begin{overpic}[width=0.8\textwidth,grid]{render.png}
    \put(10,1){Li}
\end{overpic}
```

## 软件体验

### texpad

### SWiftlatex

#### localhost-local

保存后多出空行

#### swift-google

保存失效

#### `\ref{}`未定义

强制重新编译

### BakoMa Tex

#### win64

<http://www.bakoma-tex.com/menu/win64.php>

#### china

<http://www.bakoma-tex.com/menu/cjk.php>

#### 无限试用

在前一次试用期结束之后，用软件管理员权限修改硬盘序列号，在注册表中删去 HKEY_CURRENT_USER\Software\BaKoMa\Keys 这一项，然后启动Bakoma，点击Evaluate重新下载许可证文件，就又能获得30天试用期。

- 26E0-7E64
- 26E0-7E65
- 26E0-7E66
- 26E0-7E7A
- 1C8A-47D5
- 1C8A-47D6
- 1C8A-47D7
- E8BB-53A7
- E8BB-53A8

<https://my.oschina.net/u/4266314/blog/4663380>

#### bug

pdf图像显示异常

### texmacs

非tex格式
