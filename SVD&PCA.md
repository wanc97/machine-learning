## 奇异值分解（SVD）
- 将矩阵分解为左奇异矩阵+奇异值+右奇异矩阵；

- 是一种能够从非常本质的层面展现矩阵信息的工具；

- 左奇异矩阵：将原矩阵的行看作特征，列看作样本，得到投影方差降序递减方向向量。

- 右奇异矩阵：将原矩阵的列看作特征，行看作样本，得到投影方差降序递减方向向量。

- 奇异值：对应向量的方差。

- 矩阵运算就是做空间转换，例如：右乘向量就是对向量按右奇异矩阵的方向分解，并投影到对应的左奇异矩阵方向，同时乘以相应权重（奇异值）。

## 主成分分析（PCA）
将每个样本放成一行，得到矩阵，做奇异值分解，右奇异矩阵就是各个成分，左奇异矩阵与奇异值的乘积就是各个样本在各个成分上的分量。