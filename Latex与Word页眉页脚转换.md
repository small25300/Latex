# Word与Latex页眉页脚转换计算
## Word与Latex页眉页脚的定义
  - 要求：word页边距为：3.5cm，2.5cm，2.5cm，2.5cm（分别对应上、下、左、右），页眉顶端距离：2.5cm，段后30磅，页脚底端距离：2cm，段前30磅。
  - word与latex页眉页脚定义区别：（详见图1）
    - 区别1：word中的页眉、页脚不再正文Body(正文)中，而latex包含两种格式，一种是默认与word一致，另一种是页眉页脚在Body中，latex中用\\includeheadfoot命令在geometry宏包中进行设置。
    - 区别2：word中的页眉顶端距离是指页眉字体上边沿距离A4纸张上边沿的距离，页脚底端距离指页脚字体下边沿与A4纸下边沿的距离。
<div align=center>
  <img src="https://github.com/small25300/ImageLibrary/blob/master/DefinitionOfHeadfoot/Word%E9%A1%B5%E7%9C%89%E9%A1%B5%E8%84%9A.jpg", width = 50%,height = 50%><img src="https://github.com/small25300/ImageLibrary/blob/master/DefinitionOfHeadfoot/Latex%E9%A1%B5%E7%9C%89%E9%A1%B5%E8%84%9A.jpg", width = 50%,height = 50%>
</div>
<br/> 
<p align="center">图1 Word与Latex页眉页脚定义图</p>

  - Word与Latex最大的区别是：
    - Word中页眉与页脚的段后与段前的距离会影响Body的大小，也就是说textheight（文本区域高度）会随着页眉段后、页脚段前的增大而减小。
    - Latex中textheight即Body是固定不变的，因此若word中页眉页脚有段后、段前设置，应该在转为Latex时考虑进去。
## Word与Latex页眉页脚转换具体计算
  - Word中页眉页脚不包含段后、段前设置的情况：
    - Latex中：$$headheight + headsep = Word上页边距 - Word页眉顶端距离$$，其中$$headheight = Word页眉字体大小值及行间距$$，例如5号字就是9pt。
    - Latex中：$$footskip = Word下页边距 - Word页脚底端距离。
  - Word中页眉页脚包含段后、段前设置的情况：
    - 如果Word中页眉页脚有段前、段后值，如该例中段前、段后都为30pt，则Latex中应该重新规划上下页边距，因为Word页眉页脚的段后、段前值改变了textheight，所以应该先计算Latex页眉、页脚的相关距离，再计算Latex的页边距（目的是让Latex页面设置与Word完全相同）。如图2 所示：
<div align=center>
  <img src=<img src="https://github.com/small25300/ImageLibrary/blob/master/DefinitionOfHeadfoot/%E5%8C%85%E5%90%AB%E6%AE%B5%E5%89%8D%E6%AE%B5%E5%90%8E%E7%9A%84%E8%BD%AC%E6%8D%A2.jpg", width = 50%,height = 50%>
</div>
<br/> 
<p align="center">图2 Word与Latex页眉页脚转换计算图</p>    
    - $$LatexTop = WordTop + headheight + 30pt(段后距离，实质上就是headsep)$$
    - $$LatexBottom = WordBottom + 30pt(近似：10.54mm)$$，因为页脚段前30pt相当于页边距增加30pt（textheight减小30pt），计算简单。
    
