# 如何修改latex中有bib生成的参考文献的行间距
- 在preamble(导言区)\usepackage{bibspacing}
- 但是latex并没有自带bibspacing.sty文件需要自己下载，是一串代码，需要在latex中新建文档，将代码写入，然后保存为bibspacing.sty文件。
- bib生成参考文献的行间距不能直接修改，目前还么有找到好的方法，在用custom-bib生成自己的bst文件后，编译会生成.bbl文件，在.bbl文件中添加语句进行修改。
  - 添加内容为：\setlength{\bibspacing}{0.5ex}\zihao{5},指将间距修改为0.5ex，字号大小为5号字。
- bibspacing.sty文件代码如下：
```
\newdimen\bibindent
\setlength\bibindent{1.5em}
\newdimen\bibspacing
\setlength\bibspacing\z@
\renewenvironment{thebibliography}[1]{%
  \section*{\refname
        \@mkboth{\MakeUppercase\refname}{\MakeUppercase\refname}}%
      \list{\@biblabel{\@arabic\c@enumiv}}%
           {\settowidth\labelwidth{\@biblabel{#1}}%
            \leftmargin\labelwidth
            \advance\leftmargin\labelsep 
            \itemsep\z@skip    % should this be commented out?
            \parsep\z@skip     % should this be commented out?
            \@openbib@code
            \usecounter{enumiv}%
            \let\p@enumiv\@empty
            \renewcommand\theenumiv{\@arabic\c@enumiv}}%
      \sloppy\clubpenalty4000\widowpenalty4000%
      \sfcode`\.\@m}
     {\def\@noitemerr
       {\@latex@warning{Empty `thebibliography' environment}}%
      \endlist}
```
