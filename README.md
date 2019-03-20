# Latex参考文档
- Latex最全的中文文档：http://static.latexstudio.net/wp-content/uploads/2017/08/Note-by-LaTeX-cn.pdf
- Latex比较全面的论文写作在线教程：http://www.latexstudio.net/hulatex/package/content.htm
- Latex中titlesec宏包的中文翻译：https://wenku.baidu.com/view/18361148e518964bcf847cdc.html
- Latex常用宏包的总结及一些细节：http://blog.chinaunix.net/uid-20289887-id-1710422.html
- 一份Latex入门的ppt：http://www.math.zju.edu.cn:8080/linzhi/Teaching/ZJU/latex/LaTeX_crash_course.pdf
- bibliography详解：https://www.cnblogs.com/longdouhzt/archive/2012/06/21/2557965.html
- custom-bib(制定自己风格的bib文件，以符合自己独特的要求)：
  - 说明文档：http://mirror.lzu.edu.cn/CTAN/macros/latex/contrib/custom-bib/makebst.pdf
  - custom-bib安装使用中文网站1：https://blog.csdn.net/xueshengke/article/details/74043243
  - custom-bib使用中文网站2：https://blog.csdn.net/tinkle181129/article/details/49822171/
  - 如何修改由cutom-bib生成的自己的.bst文件：https://www.zhihu.com/question/26893808
  - bst语法简介：http://blog.sina.com.cn/s/blog_6cf921f301018psq.html
  - bst中format.org.or.pub(format.organization.or.publisher)的修改
  ```FUNCTION {format.org.or.pub}
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
  }```
  - 关于取消book中作者后面editor的修改：
  ```
      FUNCTION {format.editors}
      { editor "editor" format.names duplicate$ empty$ 'skip$
          {
            "" * % 此处是editor前面的那个逗号，
            %因为我们在FUNCTION{bbl.editor和bbl.editors}中将"editor"删除了，
            %不让它显示，但是却多了一个逗号，在此处删除。
            " " *
            get.bbl.editor
            *
          }
        if$
      }
  ```
- newenvironment命令详解：http://softlab.sdut.edu.cn/blog/subaochen/2017/07/%E8%AF%A6%E8%A7%A3newenvironment%E5%91%BD%E4%BB%A4/
# Github访问上传速度慢解决方案
- https://blog.csdn.net/qq_26981913/article/details/81093932
 <div align=center><img src="https://github.com/small25300/Latex/blob/master/PaperFormat/Logo/logo.jpg?raw=true"></div>
 
