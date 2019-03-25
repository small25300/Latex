## 1.如何删除book参考文献中的作者后面的“editor”单词：
```
FUNCTION {format.editors}
{ editor "editor" format.names duplicate$ empty$ 'skip$
    {
      "" * % 此处是editor前的逗号，在FUNCTION{bbl.editor和bbl.editors}中将"editor"删除了，却多了一个逗号，在此处删除。
      " " *
      %get.bbl.editor %将book中的editors关键字不显示。
      *
    }
  if$
}
```    
## 2.如何修改title后面与publisher后面标点符号：
```
FUNCTION {format.org.or.pub}
{ 't :=
  ". "%此处是出版社后面的符号
  year empty$
    { "empty year in " cite$ * warning$ }
    'skip$
  if$
  address empty$ t empty$ and
  year empty$ and
    'skip$
    {
      address "address" bibinfo.check *
      t empty$
        'skip$
        { address empty$
            'skip$
            { ": " * }
          if$
          t *
        }
      if$
      year empty$
        'skip$
        { t empty$ address empty$ and
            'skip$
            { ", " *  *} %修改book中title与publisher句号和逗号恰好相反的问题，源代码是{ ", " * swap$ * } 
          if$
          year "year" bibinfo.check
          *
        }
      if$
    }
  if$
}
```
## 3.删除et al前面的逗号（但book中两个作者之间的逗号也跟随消失）：
```
FUNCTION {format.names}
{ 'bibinfo :=
  duplicate$ empty$ 'skip$ {
  's :=
  "" 't :=
  #1 'nameptr :=
  s num.names$ 'numnames :=
  numnames 'namesleft :=
    { namesleft #0 > }
    { s nameptr
      "{vv~}{ll}{ jj}{ f{.}.}"
      format.name$
      bibinfo bibinfo.check
      't :=
      nameptr #1 >
        {
          nameptr #3
          #1 + =
          numnames #3
          > and
            { "others" 't :=
              #1 'namesleft := }
            'skip$
          if$
          namesleft #1 >
            { ", " * t * }
            {
              s nameptr "{ll}" format.name$ duplicate$ "others" =
                { 't := }
                { pop$ }
              if$
              "," *  %etal前面的逗号删除,但是同时将book中作者间的逗号页删除了，所以此处逗号不能删除。
              t "others" =
                {
                  " " * bbl.etal *% 将两个*号之间的bbl.etal删除，则不让etal显示，但是英文参考文献需要，所以不删除，但中文参考文献却不需要，所以所有中文作者超过3个的，仅写3个最后一个加“等”字，自己维护。
                }
                { " " * t * }
              if$
            }
          if$
        }
        't
      if$
      nameptr #1 + 'nameptr :=
      namesleft #1 - 'namesleft :=
    }
  while$
  } if$
}
```
## 4.硕博论文显示学校

    * 硕士学位论文

        ```
        FUNCTION {mastersthesis} %注意：在bib中用@mastersthesis，而不是@thesis，这是硕士论文
        { output.bibitem
          format.authors "author" output.check
          new.block
          format.btitle
          "title" output.check
          new.block
          % bbl.mthesis format.thesis.type output.nonnull %将英文的Master's thesis不显示 
          school "school" bibinfo.warn output 
          address "address" bibinfo.check output
          format.date "year" output.check
          new.block
          format.note output
          fin.entry
        }
        ```
