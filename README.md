<font face="黑体" color=blue size=8>2018
SAS实验考试要点
</font>
made by dch

# 数据的预处理与数据集的导入

* 数据的预处理

>     1. 复制题中数据到Excel
>     2. Excel中将中文变量替换成英文变量，便于程序处理
>     3. 保存为xls文件格式文件，SAS9.2识别不了xlsx格式的文件

* 数据集的导入

>     1. SAS 9.2方式：

![](https://i.imgur.com/e3Gaamx.png)

>     2. SAS University方式：
>     - 先要设置共享文件夹

![](https://i.imgur.com/yCvSocM.png)
>     - 将xls文件放入共享文件夹

![](https://i.imgur.com/XcQuUyf.png)
>     - 右键导入数据，默认输出名为“IMPORT”的数据集，可以自己更改输出数据集的名字

![](https://i.imgur.com/AxubIhi.png)

# 描述统计量与正态性检验

操作不熟练的话，你<font color=red>任意选择一个变量</font>进行这两个分析即可！

* 描述统计量

>     均值、方差、标准差、变异系数、偏度、峰度

<pre><font color=red>
proc means data=你的数据集 mean ...;  
var 你的变量;  
run;
</font></pre>

<font color=green>
上面的这几个统计量最好自己课后查下符号是什么！
</font>

* 正态性检验

>     作直方图，并作拟合正态分布曲线

<pre><font color=red>
proc univariate data=你的数据集;
var 你的变量;
histogram 你的变量 / normal;
run;
</font></pre>

<font color=green>
只要把图放上来即可
</font>

# 回归分析

* 直接回归方程

<pre><font color=red>
proc reg data=你的数据集;
model 因变量=自变量;
run;
</font></pre>

<font color=green>
要求写出回归方程，根据P值解析系数的显著性
</font>

* 逐步回归方程

<pre><font color=red>
proc reg data=你的数据集;
model 因变量=自变量 / selection=stepwise;
run;
</font></pre>

<font color=green>
要求写出经过逐步回归处理后最后一步得到的回归方程，根据P值解析系数的显著性
</font>

# 主成份分析

* 相关矩阵、相关矩阵的特征值、特征向量

<pre><font color=red>
proc princomp data=你的数据集;
var 你的变量;
run;
</font></pre>

<font color=green>
结果可以截图放上来
</font>

* 主成份的挑选、线性表示及对应的累计贡献率

<font color=green>
根据0.85原则挑选主成份，将你挑选的主成份表示为原变量的线性组合，同时给出对应的累积贡献率
</font>

# 聚类分析

>     谱系聚类、聚类数、谱系图

<pre><font color=red>
proc cluster data=你的数据集 method=聚类的方法 std pseudo ccc outtree=输出的数据集;
var 你的变量;
id 你的组别;
run;
proc tree data=输出的数据集 horizontal graphics;
run;
</font></pre>

<font color=green>
要求会根据题目要求选择对应的聚类方法，会根据pseudo ccc两个指标分别说明应该选择划分多少类别较为合适，要给出聚类图
</font>