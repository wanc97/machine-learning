# 概率&统计



|      | 概率           | 统计              |
| ---- | ------------ | --------------- |
| 集中趋势 | 分布期望         | 样本均值、中位数、众数     |
| 分散度  | 分布方差/标准差、分位点 | 样本方差/标准差、全距、四分距 |

## 基本概念



**统计模型**

* $$p(x;\theta)$$：随机变量$$x$$的概率参数$$\theta$$的影响

**随机样本**

* 从统计模型中独立同分布地生成的实例；

**统计集中趋势**

* 均值：为这批数据找到它们的“代表”
  * 局限：把众多的数据用一个数据表示出来必然会丢失许多信息，如：数据分布情况会因异常值而产生巨大偏离。（张家有钱一千万，邻居九个穷光蛋，平均各个张百万）
* 中位数：中点数，中值；是按顺序排列的一组数据中居于中间位置的数。
  * 局限：当数据有多个不同的部分组成时，中位数也没有太多的代表性。
* 众数：样本观测值在频数分布表中频数最多的那一组的组中值。

**统计分散度** 平均数可以表征一批数据的典型值，但是仅凭平均数还不能给我们提供足够的信息，平均数无法表征一组数据的分散程度。

* 全距=max-min：也叫极差。它是一组数据中最大值与最小值之差。可以用于度量数据的分散程度。
  * 局限：全距虽然求解方便快捷，但是它的局限性在于“若数据中存在异常值的情况，会产生偏差。为了摆脱异常值带来的干扰，比如我们看一下下面的两组数据。只是增加了一个异常值，两组数据的全距产生了巨大的差异。
* 四分位数：所有观测值从小到大排序后四等分，处于三个分割点位置的数值就是四分位数：Q1，Q2和Q3。
* 迷你距：也叫四分位距；一组数据中较小四分位数与较大四分位数之差；迷你距= 上四分位数 - 下四分位数。
* 全距，四分位距，箱形图可以表征一组数据极大和极小值之间的差值跨度，一定程度上反应了数据的分散程度，但是却无法精准的告诉我们，这些数值具体出现的频率；我们度量每批数据中数值的“变异”程度时，可以通过观察每个数据与均值的距离来确定，各个数值与均值距离越小，变异性越小数据越集中，距离越大数据约分散，变异性越大。
  * 方差：方差是度量数据分散性的一种方法，是数值与均值的距离的平方数的平均值。
  * 标准差：方差的开方。
* 标准分：$$Z=\frac{X-\mu}{\sigma}$$，表征了距离均值的标准差的个数，可以用于有不同均值和不同标准差的多个数据集之间的数据比较。

**概率&似然**

* 概率是描述在确定分布下某个事件发生可能性的大小；
* 似然是描述在发生某些事件的情况下分布取某组参数的可能性。

**P-value**

* 一个事件的P-value不是这个事件的概率值，而是所有概率小于等于该事件概率值得概率和（积分），即反应该事件发生的稀有程度。

**划分**

* 互斥且并集为整个样本空间的一组事件称为样本空间的一个划分

**条件概率**

* 在事件A发生时事件B发生的条件概率为：事件A和事件B共同发生时的联合概率除以事件A发生的概率；
* 当事件A和事件B独立时，其联合概率等于各自发生概率的乘积，因此事件B发生的条件概率也等于事件B本身的概率。

**全概率公式**

* 一个事件的概率可以分为在一个划分下不同事件的概率与该在该事件下的条件概率乘积的和。

**矩**

* 即一种关于随机变量的期望；
* 原点矩：n阶原点矩就是随机变量的n次方的期望，如期望是一阶原点矩；
* 中心距：即随机变量通过期望去中心化后的期望，如方差是二阶中心距；

**不相关&独立**

* 不相关：$$E(x,y)=E(x)E(y)$$主要是指没有线性关系，统计上的没有关系。
* 独立：$$P(x,y)=\frac{P(x,y)P(y)}{P(y)}=P(x|y)P(y)=P(x)P(y)$$，没有任何关系，一个事件的情况不影响另一个事件的概率。

**自变量/协变量/因变量**

* 在函数$$y=f(x,b)$$中$$x$$和$$b$$都可以影响$$y$$，我们操纵$$x$$作为输入，而$$b$$独立存在不控制；称$$x$$为自变量，b为协变量，$$y$$为因变量；

## 概率分布

* 随机事件发生的概率符合一定分布；
* 期望、方差等是描述分布的指标，但不等于分布；
* $分布=分布描述+参数$，分布描述如：高斯分布、二项分布等，分布描述决定分布的基本属性，参数决定分布的具体细节；
* 连续分布：高斯分布、指数分布；离散分布：0-1/伯努利分布、二项分布、几何分布、泊松分布；

### 高斯分布

* 一维：$$P(x)=\frac{1}{\sqrt{2\pi}\sigma}e^{-\frac{1}{2}(\frac{x-\mu}{\sigma})^2}$$
* 高维：$$P(x)=\frac{1}{\sqrt{(2\pi)^d|\Sigma|}}e^{-\frac{1}{2}(x-\mu)^T\Sigma^{-1}(x-\mu)}$$
  * 其中$$\Sigma$$是对称的协方差矩阵，所以一定可以相似对角化，得到几个不相关的高斯分布；
  * 等密度点为超椭球形；
  * 边缘分布与条件分布都是高斯分布
  * 高斯分布的不相关等于独立
  * 高斯分布的线性变换/组合仍然是高斯分布；

### 伯努利分布

* $$P(x=1;\theta)=\theta,P(x=0;\theta)=1-\theta$$

### 指数分布族

* 意义：保凸性
* 基本形式：$$p(x;\theta)=h(x)e^{\eta(\theta)T(x)-A(\theta)}$$
* 伯努利分布：$$p(x;\theta)=e^{I(x=1)ln(\theta)+I(x=0)ln(1-\theta)}$$












