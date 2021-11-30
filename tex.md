
<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Table of contents](#table-of-contents)
- [template](#template)
  - [beamer](#beamer)
  - [article](#article)
  - [include](#include)
- [tikz](#tikz)
- [font](#font)
- [中文](#中文)
- [cite](#cite)
  - [biblatex](#biblatex)
  - [footcite](#footcite)
    - [多引用,](#多引用)
    - [字号](#字号)
    - [notitle](#notitle)
    - [footcitetext](#footcitetext)
  - [footfullcite](#footfullcite)
    - [多引用,](#多引用-1)
    - [footfullcitetext](#footfullcitetext)
- [overpic](#overpic)
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
- [换行](#换行)
- [常见错误](#常见错误)
- [comment](#comment)
- [date](#date)
- [item](#item)
  - [nobullet](#nobullet)
- [symbol](#symbol)
  - [pvec](#pvec)
  - [双分数](#双分数)
  - [space](#space)
  - [unit](#unit)
  - [braket](#braket)
  - [chem](#chem)
  - [integral](#integral)
  - [subscript](#subscript)
  - [overline](#overline)
  - [degree](#degree)
  - [angstrom](#angstrom)
  - [arrow](#arrow)
  - [icon](#icon)
- [highlight](#highlight)
  - [superlink](#superlink)
- [double column](#double-column)
- [equation](#equation)
  - [big bracket](#big-bracket)
- [listings](#listings)
  - [listing style](#listing-style)
  - [example](#example)
  - [Note in beamer](#note-in-beamer)
  - [multicol](#multicol)
  - [listing内命令](#listing内命令)
- [proof](#proof)
- [table](#table)
- [figure](#figure)
  - [gif](#gif)
  - [subfigure](#subfigure)
  - [wrap figure](#wrap-figure)
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


# Table of contents

```tex
\tableofcontents
```

```tex
\addcontentsline{toc}{chapter{test}
\chapter*{test}
```

# template

## beamer

```tex
%---------------------------------------------------------------------------------------------------[Package]
%-------------------------------------------------------------------------------------[type]
\documentclass[aspectratio=169]{beamer}
\usepackage[T1]{fontenc}
%-------------------------------------------------------------------------------------[移除导航]
\setbeamertemplate{navigation symbols}{}
%-------------------------------------------------------------------------------------[theme]
\usetheme{Madrid}
\usecolortheme{beaver}
%---------------------------------------------------------------------------------------------------[Head]
%-------------------------------------------------------------------------------------[titleset]
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

%-------------------------------------------------------------------------------------[titlepage]
\frame{\titlepage}

\begin{frame}
  \frametitle{Table of Contents}
  \tableofcontents[subsectionstyle=show/show/hide]
\end{frame}
%---------------------------------------------------------------------------------------------------[section]
\section{First section}
%-------------------------------------------------------------------------------------[p3]
\begin{frame}{}

\end{frame}

%---------------------------------------------------------------------------------------------------[END]
\end{document}
```

## article

```tex
%---------------------------------------------------------------------------------------------------[Package]
%-------------------------------------------------------------------------------------[size]
\documentclass[a4paper]{article}
\usepackage[T1]{fontenc}
%-------------------------------------------------------------------------------------[页边距]
\usepackage[cm]{fullpage}
%---------------------------------------------------------------------------------------------------[Head]
%-------------------------------------------------------------------------------------[title]
\title{}
\author{}
\date{}
%-------------------------------------------------------------------------------------[begindocument]
\begin{document}
%-------------------------------------------------------------------------------------[maketitle]
\maketitle
%---------------------------------------------------------------------------------------------------[START]
%-------------------------------------------------------------------------------------[abstract]
\begin{abstract}
\end{abstract}

%---------------------------------------------------------------------------------------------------[END]
\end{document}
```

## include

```tex
\input{~/codes/group/common/beamer_header}
```

# tikz

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

# font

% <https://en.wikibooks.org/wiki/LaTeX/Fonts>

```tex
%-------------------------------------------------------------------------------------[global bold]
\renewcommand{\seriesdefault}{\bfdefault}

%-------------------------------------------------------[math bold]
\mathversion{bold}

% https://tex.stackexchange.com/questions/376665/how-to-make-math-text-thick-globally-besides-mathversionbold

%-------------------------------------------------------------------------------------[fonttype]
% need XeLaTeX
\setmainfont{Arial}

%-------------------------------------------------------[math fonttype]
\usepackage{unicode-math}

\setmathfont{GFSNeohellenicMath.otf}
\setmathfont[range=up]{Arial}
\setmathfont[range=it]{Arial Italic}
\setmathfont[range=bfup]{Arial Bold}
\setmathfont[range=bfit]{Arial Bold Italic}

% https://tex.stackexchange.com/questions/469775/how-to-use-math-mode-and-siunitx-with-arial

%-------------------------------------------------------------------------------------[global fontsize]
\documentclass[12pt]{article}

\renewcommand{\small}{\fontsize{12pt}{0pt}\selectfont}

%-------------------------------------------------------------------------------------[equation & table]

\begin{small}
    \begin{table}
    \end{table}
\end{small}

\begin{small}
    \[
    \]
\end{small}
%-------------------------------------------------------------------------------------[print fontsize]
\makeatletter
\newcommand\thefontsize{\f@size pt}
\makeatother

% https://tex.stackexchange.com/questions/24599/what-point-pt-font-size-are-large-etc
```

# 中文

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

# cite

## biblatex

```tex
\usepackage[style=phys,autocite=plain]{biblatex}
\addbibresource{references.bib}
```

```tex
\autocite{}
```

```tex
\printbibliography
```

## footcite

```tex
\usepackage[style=verbose,autocite=footnote,doi=false,url=false]{biblatex}
```

### 多引用,

```tex
\usepackage{fnpct}
\AdaptNote\autocite{oo+m}[footnote]{%
\setfnpct{dont-mess-around}%
\IfNoValueTF{#1}
{#NOTE{#3}}
{\IfNoValueTF{#2}{#NOTE[#1]{#3}}{#NOTE[#1][#2]{#3}}}%
}
```

### 字号

```tex
% 7pt 字号，9pt baselineskip
\renewcommand{\footnotesize}{\fontsize{7pt}{9pt}\selectfont}
```

### notitle

```tex
\AtEveryBibitem{\clearfield{title}}
\AtEveryCitekey{\clearfield{title}}
```

### footcitetext

```tex
\newcounter{colcites}

\addtocounter{colcites}{-\thecolcites}

\footnotemark
\addtocounter{colcites}{1}
\footnotemark
\addtocounter{colcites}{1}

\addtocounter{footnote}{-\thecolcites}

\addtocounter{footnote}{1}
\footcitetext{test1}
\addtocounter{footnote}{1}
\footcitetext{test2}
```

## footfullcite

```tex
\usepackage[style=chem-acs,doi=false,url=false]{biblatex}
```

### 多引用,

```tex
\usepackage{fnpct}
\AdaptNote\footfullcite{oo+m}[footnote]{%
\setfnpct{dont-mess-around}%
\IfNoValueTF{#1}
{#NOTE{#3}}
{\IfNoValueTF{#2}{#NOTE[#1]{#3}}{#NOTE[#1][#2]{#3}}}%
}
```

### footfullcitetext

```tex
% https://tex.stackexchange.com/questions/420162/footfullcite-not-showing-when-used-within-a-wrapfigure
\DeclareCiteCommand{\footfullcitetext}[\mkbibfootnotetext]
  {\usebibmacro{prenote}}
  {\usedriver
     {\DeclareNameAlias{sortname}{default}}
     {\thefield{entrytype}}}
  {\multicitedelim}
  {\usebibmacro{postnote}}
```

```tex
\footfullcitetext{test1}
```

# overpic

```tex
%-------------------------------------------------------------------------------------[overpic]
\usepackage{overpic}
\begin{overpic}[width=0.8\textwidth,grid]{render.png}
    \put(10,1){Li}
\end{overpic}
```

# variable

```tex
%------------------------------------------[]
\newcommand{\x}{30}
%------------------------------------------[]
\newcommand{\x}[3][d]{(#2 + #3)^#1}

\[ \x{a}{b}{c} \]
%------------------------------------------[]
\newcommand{\LLZO}{C:/Users/laven/OneDrive/group/202012_LLZO}
\addbibresource{\XasPtO/doc/references.bib}
```

# 0补全

```tex
\makeatletter
\renewcommand\theimonth{\two@digits{\value{imonth}}}    
\makeatother
```

<https://tex.stackexchange.com/questions/30930/how-to-output-a-counter-with-leading-zeros>

# loop

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

# fileexist

```tex
\IfFileExists{./filename}{true-branch}{false-branch}
```

# html

```html
<img src="https://render.githubusercontent.com/render/math?math=e^{i \pi} = -1">
```

<https://gist.github.com/a-rodin/fef3f543412d6e1ec5b6cf55bf197d7b>
<https://github.com/TeamMeow/vscode-math-to-image>

# pagesize

```tex
\usepackage[margin=0in,paperwidth=3.25in,paperheight=1.75in]{geometry}
```

## 首行缩进

```tex
\parindent 0in
```

## 页边距

```tex
\usepackage{geometry}
\geometry{a4paper,left=0cm,right=0cm,top=0cm,bottom=0cm}
```


# filecontents

强制 overwrite

```tex
\makeatletter
\let\oldfilec@ntents\filec@ntents
\gdef\filec@ntents{\filec@ntents@overwrite\oldfilec@ntents}
\makeatother

\begin{filecontents}{temp_filecontents.tex}
\end{filecontents}
```

# logo

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

# 换行

- 空行 最合理
- `\par` 等同于空行
- `\\` 对齐时使用

# 常见错误

```tex
\_
\&
```

# comment

```tex
\usepackage{comment}

\begin{comment}
\end{comment}
```

# date

```tex
\usepackage[USenglish,UKenglish,french,spanish,italian]{babel}
\usepackage[useregional]{datetime2}


% after begindocument
\selectlanguage{USenglish}
\DTMdate{2021-5-6}
```

<https://tex.stackexchange.com/questions/141824/how-to-write-a-non-today-date-in-latex-with-localization-formatting>

# item

```tex
\begin{itemize}
    \item something
\end{itemize}
```

<https://www.overleaf.com/learn/latex/lists>

## nobullet

```tex
\item[]
```

<https://tex.stackexchange.com/questions/50269/itemize-without-bullets>

# symbol

## pvec

```tex
\newcommand{\pvec}[1]{\vec{#1}\mkern2mu\vphantom{#1}}
```

## 双分数

```tex
\newcommand{\ddfrac}[2]{\frac{\displaystyle #1}{\displaystyle #2}}
```

## space

```tex
\quad
\medskip
```

<https://tex.stackexchange.com/questions/74353/what-commands-are-there-for-horizontal-spacing>

## unit

```tex
\usepackage{siunitx}
\SI{0.97}{g.cm^{-3}}
```

## braket

```tex
\usepackage{braket}
\braket{d}
```

## chem

```tex
\usepackage[version=4]{mhchem}
\ce{H2O\text{*} -> H\text{*} + OH\text{*}}
```

## integral

```tex
\newcommand*{\diff}{\mathop{}\!\mathrm{d}}
$\diff x$
```

## subscript

```tex
\textsubscript
\textsuperscript
```

## overline

```tex
$\overline{2}$
\bar{2}
```

## degree

```tex
\textdegree
```

<https://tex.stackexchange.com/questions/384873/what-is-the-degree-symbol/384874>

## angstrom

```tex
\AA
```

## arrow

```tex
$
    \xleftarrow{n=0}
    \xrightarrow[T]{n>0}
$
```

<https://www.cnblogs.com/wt869054461/p/9544846.html>

## icon

```tex
\usepackage{fontawesome}

\faPhone
\faEnvelope
\faHome
\faGlobe
```

# highlight

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

# double column

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

# equation

```tex
\usepackage{amsmath}
```

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

## big bracket

```tex
\begin{align}
    \left\{
    \begin{aligned}
    \end{aligned}
    \right.
\end{align}
```

# listings

## listing style

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

## example

```tex
\lstinputlisting[language=bash,caption=]{file}
```

```tex
\begin{lstlisting}[language=bash]
\end{lstlisting}
```

<https://www.overleaf.com/learn/latex/Code_listing>

## Note in beamer

```tex
\begin{frame}[fragile]
\end{frame}
```

<https://tex.stackexchange.com/questions/130109/cant-insert-code-in-my-beamer-slide>

## multicol

```tex
\usepackage{multicol}
\lstinputlisting[multicols=4]{data.txt}
```

## listing内命令

```tex
\begin{lstlisting}[escapechar=\%]
%\leftarrow%
\end{lstlisting}
```

# proof

```tex
\usepackage{amssymb,amsthm}
```

# table

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

```tex
\usepackage{multirow}

\begin{block}{}
    \begin{table}[ht]
    \centering
    \begin{tabular}{c|cc}
    \hline
        &\multicolumn{2}{c}{} \\
    \hline
    \multirow{2}{*}{}
        &   &   \\
        &   &   \\
    \hline
    \end{tabular}
    \end{table}
\end{block}
```

# figure

```tex
\usepackage{graphicx}

\begin{figure}[ht]
    \centering
    \includegraphics[width=0.75\textwidth,height=0.75\textheight]{Xas_Pt_O_vac/Xas_Pt_O_vac}
    \caption{}
    \label{fig:}
\end{figure}
```

## gif

```tex
\usepackage{animate}

\begin{figure}
    \animategraphics[loop,controls={play,step,speed},width=0.8\textwidth]{20}{test}{0008}{0032}
    \centering
\end{figure}
```

## subfigure

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

## wrap figure

```tex
\usepackage{wrapfig}

\begin{wrapfigure}{r}{0.25\textwidth} %this figure will be at the right
    \centering
    \includegraphics[width=0.25\textwidth]{mesh}
\end{wrapfigure}
```

# 软件体验

## texpad

## SWiftlatex

### localhost-local

保存后多出空行

### swift-google

保存失效

### `\ref{}`未定义

强制重新编译

## BakoMa Tex

### win64

<http://www.bakoma-tex.com/menu/win64.php>

### china

<http://www.bakoma-tex.com/menu/cjk.php>

### 无限试用

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

### bug

pdf图像显示异常

## texmacs

非tex格式
