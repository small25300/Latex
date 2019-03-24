# Word与latex页眉页脚转换计算
  - 要求：word页边距为：3.5cm，2.5cm，2.5cm，2.5cm（分别对应上、下、左、右），页眉顶端距离：2.5cm，段后30磅，页脚底端距离：2cm，段前30磅。
  - word与latex页眉页脚定义区别：
    - 区别1：word中的页眉、页脚不再正文Body(正文)中，而latex包含两种格式，一种是默认与word一致，另一种是页眉页脚在Body中，latex中用\\includeheadfoot命令在geometry宏包中进行设置。
