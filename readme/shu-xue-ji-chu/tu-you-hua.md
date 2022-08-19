# 凸优化

## **凸优化问题**

* 凸函数在凸集上优化
* 凸集要求：
  * 等式约束：仿射函数
    * 仿射函数：最高次数为1的多项式函数。
    * 常数项为零的仿射函数称为线性函数。
  * 不等式约束为:凸函数<=0 或 凹函数>=0
* 具体形式如下： $$min_{\vec{w}}f(\vec{w})$$ $$s.t.\qquad g_j(\vec{w})\le0,j=1,2,...,J\qquad h_k(\vec{w})=0,k=1,2,...,K$$
* 其中$$f(\vec{w})$$和$$g_j(\vec{w})$$都是$$R^n$$上的连续可微凸函数；$$h_k(\vec{w})$$是仿射函数。

## **拉格朗日乘子法**

* 可以将带约束求极值的问题转化为无约束求极值问题
* 通过引入松弛变量$$\lambda\ge0$$和拉格朗日乘子$$\mu$$可设计函数： $$L(\vec{w},\lambda,\mu)=f(\vec{w})+\sum_j\lambda_jg_j(\vec{w})+\sum_k\mu_kh_k(\vec{w})$$
* 同时由于一种奇妙的性质： $$max_{\lambda,\mu}L(\vec{w},\lambda,\mu)={f(\vec{w}),\vec{w}满足约束 \atop \infty,\vec{w}不满足约束}$$
* 使得原问题转化为了无约束的问题： $$min_{\vec{w}}max_{\lambda,\mu}L(\vec{w},\lambda,\mu)$$
* 对偶问题即通过交换极小、极大地顺序而来,通过对偶问题往往能降低难度： $$max_{\lambda,\mu}min_{\vec{w}}L(\vec{w},\lambda,\mu)$$
* 弱对偶性： $$max_{\lambda,\mu}min_{\vec{w}}L(\vec{w},\lambda,\mu)\le min_{\vec{w}}max_{\lambda,\mu}L(\vec{w},\lambda,\mu)$$
* 强对偶性： $$max_{\lambda,\mu}min_{\vec{w}}L(\vec{w},\lambda,\mu)=min_{\vec{w}}max_{\lambda,\mu}L(\vec{w},\lambda,\mu)$$
* 对于满足强对偶性的情况，对偶问题得到的解就是原问题的解；对于不满足强对偶性，对偶问题的解不一定是原问题的解。
* 对于凸优化问题，KKT条件与强对偶性互为充要；对于非凸优化问题，KKT条件是强对偶性的必要条件，还需要加上二阶导数正定判断。

## **KKT条件原理**

* KKT条件为：
  * $$\nabla_{\vec{w}}{L(\vec{w},\lambda,\mu)}=0$$
  * $$\lambda_j\ge 0,j=1,2,...,J$$
  * $$\lambda_jg_j(\vec{w})=0,j=1,2,...,J$$
  * $$g_j(\vec{w})\le0,j=1,2,...,J$$
  * $$h_k(\vec{w})=0,k=1,2,...,K$$
* 对于等式约束：
  * 等同于将可行域限定在等式约束所代表的超平面上；
  * 如果极值点处的梯度与超平面不垂直，则此处还有优化空间，即此处不是极值点；
  * 所以极值点处函数的梯度一定与超平面垂直，即函数的梯度一定与超平面的梯度共线；
  * 如果有多个等式约束，则函数的梯度在各个超平面梯度组成的子空间中。
  * 由此可以得到等式约束极值必要条件（第一条）。
* 对于不等式约束（统一采用小于或等于）
  * 可以将约束分成起作用的约束和不起作用的约束；
  * 对于起作用的不等式约束，分析方法同等式约束，即函数的梯度一定与约束函数的梯度反向（不仅要共线，因为如果梯度同向则此约束暂时不起作用）
  * 如果多个不等式约束同时作用，则函数的负梯度一定在各个约束的梯度正向子空间内，即加权系数一定要是正的。
  * 对于不起作用的约束，加权系数为0。
  * 由此分析可以得到不等式约束极值必要条件KKT条件（前三条）（凸优化时是充要条件）
* 另外加上原约束条件和极值的正定约束条件，可得全部条件；
* 等式约束要求梯度一定共线但不要求同反向，不等式约束不起作用不要求，起作用必反向；
* 等式约束可以看成是两个不等式约束来分析，此时必起作用。