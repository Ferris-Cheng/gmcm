# 遗传算法-GA

是一种通过模拟自然进化过程搜索最优解的方法

遗传算法的基本原理：首先根据问题产生多个初始可行解()，然后从初始解中选择诺干优异的个体(问题的解)进行各种操作(交叉，变异)用以产生新的后代。再从新的后代中选择优异的个体进行相应的操作产生它们的后代，如此不断循环，直到迭代的次数达到了预先设定的值或者多次迭代以后产生的最优异的个体(最优解)的质量并没有明显的提高，就可以停止迭代，这时的最优个体(最优解)最为问题的解

适用范围：对于没有确切解的问题，反复迭代求解最优解的一种方法

属于全局优化方法，同属于全局优化方法的还有：漫步法、模拟退火法。主要特点是不依赖初始条件，可以获得全局最优解，但速度慢
局部优化方法：牛顿法、梯度下降法。主要特点是条件严格，需要可微，但收敛速度快
  
## Case1：基于遗传算法的TSP问题

TSP(旅行商问题，Traveling Salesman Problem)：给定一系列城市和每对城市之间的距离，求解访问每一座城市一次并回到起始城市的最短回路。它是组合优化中的一个NP困难问题

1.选择一种合适的编码方式

基于符号编码：对于TSP问题，我们直接使用路径来表示一个染色体。即使用一个整数数组，数组长度为TSP城市的数量，数组中存储各个城市编号，从下标为0开始逐个遍历数组元素形成的一个序列即为路径(对于要回到原点的要求，为了方便表示，在这里不作考虑，只是在计算路径长度的时候会添加相应的长度)

2.形成初始解

采用随机的方式产生诺干个(种群规模)的序列，即产生符合城市编号的随机数存储在数组中，数组中的元素包含所有的城市编号，而且没有重复的编码。数组的个数为种群规模

3.选择

在形成一定数量的可行解（染色体）后，需要对这些父代的染色体进行筛选。根据生物遗传的基因的优胜劣汰原则，在筛选染色体的我们也会秉承精英保留原则，使得优异的基因有更多的机会得到遗传。

　　适应度函数： 这里我们选择路径长度的倒数来作为解的适应度

　　在这个问题中，我们选择“轮盘赌”算法来筛选染色体。

　　基本原理：计算每个染色体(路径)的长度的倒数，再得到所有路径倒数之和，用每条路径的倒数除以所有所有路径倒数之和即为这条路径被选中的概率(路径越短，概率越高)。
  
4.交叉

这里我们选择交替位置交叉法（Alternating Position Crossover，APX）来对一对染色体进行交叉操作，其基本原理如下图所示

　　左边为父代的两个染色体，右边为子代染色体。 将左上的数组第一个元素放入右上数组的第一位置中，再转移到左下数组第一个元素，查看右上数组是否已经包含了该元素，如果未包含将其插入右上数组中，否则插入右下数组中。接着从左上数组的第二个元素开始，到左下第二个元素，和前次同意的判断操作。如此类推直到右边两个数组都被填满了为止。

　　交叉概率：交叉概率对于解的收敛速度有着重要的影响。一般选择0.6-1。

4.变异

生物的进化，除了遗传父母的基因，还有自身基因有一定的概率突变。基于这个原理，变异操作在一定的概率上是作用于染色体自身的。

　　变异概率：一定的概率师兄自身基因的改变

　　在这个问题中，我们选择位置倒换法，即染色体上随机的产生两个位置上数值互换。
  
5.终止条件

一般有两种方式停止交叉，变异的操作。一，预先设定迭代次数。二，多次跌代后，解的质量得不到一定要求的提高，或者解达到要求的质量，这时都可以停止迭代。这个问题上我们选择第一种。

## Case2：基于遗传算法的BP神经网络优化算法

## Case3：基于遗传算法的
