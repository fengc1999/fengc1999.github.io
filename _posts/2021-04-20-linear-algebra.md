---
layout:     post
title:      线性代数的本质学习笔记
subtitle:   
date:       2021-04-20
author:     FengC
header-img: img/post-bg-ios9-web.jpg
catalog: 	true
tags:
    - 线性代数
---

# 一、向量
* **向量**  
可以是列表，箭头等多种具体形式，也可以是函数这种抽象形式。线性代数中更愿意解释向量为起点固定在原点，由终点表示的孤立点，这有利于在几何层次上进行理解。

* **向量空间**  
数学家将符合以下八条性质的事物的集合统一称为向量空间，可以简单理解为符合数乘和相加的运算原则。
![]({{ site.url }}/img/20210420/1.png)

* **线性组合**  
向量数乘和加法的混合运算

$$
m_1\vec{x_1}+m_2\vec{x_2}+\cdot\cdot\cdot+m_n\vec{x_n}
$$
    
此结果可以得到的所有结果的集合即$x_1$, $x_2$,...,$x_n$张成（span）的线性空间，如果此空间维度等于n，则$x_1$, $x_2$,...,$x_n$向量组线性无关；若大于n，则线性相关，即有多余的向量可以被其他向量的线性组合表示出来。

* **空间的基（向量）**  
张成该空间的一组线性无关向量集

# 二、矩阵
* **对矩阵的理解**：  
一个矩阵对应一种线性变化，一种线性变化对应一个矩阵（矩阵是计算形式，线性变化是物理解释）。线性变化的本质是线性函数，满足数乘和加法运算，对向量的变化实际上是对基的变化，所以**矩阵是线性变化后的基构成的列向量组**，右乘的向量是线性组合系数。
    > 线性变化：保持网格平行且等距分布的变化。

* **矩阵相乘**  
需要从右往左理解，即依次进行线性变化，自然矩阵乘法满足结合律。

* **逆矩阵**  
对应的线性变化与原矩阵的线性变化恰好相反。行列式为0不存在逆矩阵，因为这意味着此变化是降维，会丢失信息。
    >transformation即变化的本质是函数，输入一种状态，只输出一种状态。逆变化也是transformation，但是一种降维可以映射多种升维，所以不存在逆变化。

* **非方阵**  
比反阵多一个升降维的变化，比如$1\times2$的矩阵即把二维空间的沿着某个方向的平行线压缩成一个个的点。

* **矩阵的列空间和秩（Rank）**  
列向量组张成的空间，维度即秩（不大于矩阵的列数和行数）。当秩与列数相等时，就称满秩。

* **矩阵的零空间（Null space）或核（Kernel）**  
变化后会落在原点的向量组成的集合，一般形成一条直线、一个平面等这样的线性空间。对于满秩方阵不会发生维度变化，所以只有零向量会在变化后落在原点。

# 三、行列式
* **行列式的意义**  
衡量一个矩阵对应的线性变化给任意形状造成的超体积变化比列，二维对应面积变化，三维则是体积变化。（由于网格线始终平行等距的性质，导致所有形状的超体积变化比例一致）

![]({{site.url}}/img/20210420/2.png)

* **行列式为0**  
说明对应的变化将空间压缩到了更低维度，同时说明矩阵的列向量组线性相关。非方阵也可以改变维度，但是没有行列式，因为不在一个空间内，无法比较超体积。

* **行列式为负**
空间发生了翻转

* **矩阵乘积的行列式**  
结合行列式的意义即可明白：

$$
det(M_1M_2)=det(M_1)det(M_2)
$$

# 四、点积与叉积
* **点积的意义**  
$\vec{a}\cdot\vec{b}$实际上就是b在a上的投影与a的模长乘积，且由于满足对偶性（duality），反之也成立，且$\vec{a}\cdot\vec{b}=\vec{b}\cdot\vec{a}$
    > 点积是理解投影的工具，主要用于判断两个向量的方向关系。

* **n维向量与$1\times n$矩阵的关系**  
多维空间到一维空间的线性变换的对偶是多维空间中的某个特定向量，由对偶性可得到，$\vec{a}$在$\vec{b}$上的投影矩阵就是$\vec{a}$的单位向量$\vec{u}$的转置：

![]({{site.url}}/img/20210420/3.png)

* **叉积的意义**
$\vec{a}\times\vec{b}$叉积的结果是一个向量，垂直于$\vec{a}$和$\vec{b}$，大小为$\vec{a}$和$\vec{b}$构成的平行四边形面积（由$det(\{\vec{a}\vec{b}\}可得)$），符合右手原则：

![]({{site.url}}/img/20210420/4.png)

* **线性变化角度看叉积**  
定义一个线性函数，可以计算$[x, y, z]^T$与固定向量$\vec{v}$和$\vec{w}$构成的平行六面体的体积。由于线性函数实际就是一个线性变化，所以可以用一个矩阵代替，且为$1\times3$的矩阵，而由对偶性，其实际上对应于一个3维向量。可以由点积计算出这个向量的值：

![]({{site.url}}/img/20210420/5.png)

实际上这个计算出的向量从几何意义上分析，它位于$\vec{v}$和$\vec{w}$垂直方向上的，且由于和$[x, y, z]^T$点积结果为平行六面体的体积，所以其大小为$\vec{v}$和$\vec{w}$构成的平行四边形面积，这不就是需要求的叉积嘛：

![]({{site.url}}/img/20210420/6.png)

# 五、基变换
* **$A^{-1}MA$**  
意味着一种数学转移，即从其他基的角度看待常见的线性变化。A表示基构成的矩阵，M表示线性变化。

# 六、特征向量
* **特征向量的意义**  
对于任意的矩阵M，对应都一种线性变化，可以对原空间的任意向量作转换，如果空间中存在向量在转换后仍可以留在自己张成的空间（一条直线）上，这样的向量就是M的**特征向量**（包括其张成空间所有的向量）。而M对于特征向量的作用就相当于作伸缩，伸缩的比例就是**特征值**。

![]({{site.url}}/img/20210420/7.png)

由公式可得，转换结果为$\vec{0}$，相当于此时$\vec{v}$张成的直线被压缩到原点，就需要$A-\lambda I$降维，所以其行列式为0，解的个数对应特征值存在的数量。

* **特征基**
由基向量（同时也是特征向量）构成的集合。
    >在特征基构成的坐标系下，特征基矩阵是对角矩阵，且对角矩阵的特征向量就是它的列向量组。

* **对角矩阵求矩阵的幂**  
可以由原矩阵得到特征基，利用基转换得到对角矩阵，求幂运算会大大降低。

## 参考资料
1. [3Blue1Brown线性代数教学合集](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)
2. [bilibili熟肉翻译](https://www.bilibili.com/video/BV1ys411472E)