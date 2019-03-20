## 1.如何删除book参考文献中的作者后面的“editor”单词：
```
    FUNCTION {format.editors}
    { editor "editor" format.names duplicate$ empty$ 'skip$
        {
          "" * % 此处是editor前的逗号，在FUNCTION{bbl.editor和bbl.editors}中将"editor"删除了，但是却多了一个逗号，在此处删除。
          " " *
          get.bbl.editor
          *
        }
      if$
    }
```    
## 1.如何修改title后面与publisher后面标点符号：
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
