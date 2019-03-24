# Word与latex页眉页脚转换计算
  - 要求：word页边距为：3.5cm，2.5cm，2.5cm，2.5cm（分别对应上、下、左、右），页眉顶端距离：2.5cm，段后30磅，页脚底端距离：2cm，段前30磅。
  - word与latex页眉页脚定义区别：（详见图1）
    - 区别1：word中的页眉、页脚不再正文Body(正文)中，而latex包含两种格式，一种是默认与word一致，另一种是页眉页脚在Body中，latex中用\\includeheadfoot命令在geometry宏包中进行设置。
    - 区别2：word中的页眉顶端距离是指页眉字体上边沿距离A4纸张上边沿的距离，页脚底端距离指页脚字体下边沿与A4纸下边沿的距离。
<div align=center>
  <img src="https://github.com/small25300/ImageLibrary/blob/master/DefinitionOfHeadfoot/Word%E9%A1%B5%E7%9C%89%E9%A1%B5%E8%84%9A.jpg", width = 50%,height = 50%><img src="https://github.com/small25300/ImageLibrary/blob/master/DefinitionOfHeadfoot/Latex%E9%A1%B5%E7%9C%89%E9%A1%B5%E8%84%9A.jpg", width = 50%,height = 50%>
</div>
<br/> 
<center> 图1 Word与Latex页眉页脚定义图 </center>


<center> 图1Word与Latex页眉页脚定义图 </center>
