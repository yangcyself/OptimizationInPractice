# Truth discovery with sparsity and redundancy

## Problem


**Input:** Observations for N entities by M workers $x_{ij}$, Similarity information among entities

**Output:** The value of each entity $x_{j}^{*}$

> hint: Incoorporate Matrix Factorization into the problem

## Optimization


The problem becomes:

$$
\min \quad \mathbf{M F}+\mathbf{R} \mathbf{1}+\mathbf{R} \mathbf{2}
$$

where:
$$\mathbf{M F}:\left\|H \circ\left(X-U V^{\mathrm{T}}\right)\right\|^{2}+\alpha\left(\|U\|^{2}+\|V\|^{2}\right)$$
 
is **Regularized PCA**

$$
\begin{aligned}
\mathbf{R} \mathbf{1}: & \sum_{j=1}^{N} \sum_{j^{\prime}=1}^{N} a_{j j^{\prime}}\left\|V_{j \cdot}-V_{j^{\prime} \cdot}\right\|^{2} \\
&=\sum_{j=1}^{N} \sum_{j^{\prime}=1}^{N}\left[a_{j j^{\prime}} \sum_{k=1}^{K}\left(V_{j k}-V_{j^{\prime} k}\right)^{2}\right] \\
&=\sum_{k=1}^{K} V_{\cdot k}^{\mathrm{T}} L V_{\cdot k} \\
&=\operatorname{tr}\left(V^{\mathrm{T}} L V\right)
\end{aligned}
$$

is the correlation term

$$
\begin{aligned}
\mathbf{R 2}: & \sum_{j=1}^{N} \sum_{k=1}^{K}\left(v_{j k}-v_{j}^{*}\right)^{2} w_{k} \\
&=\operatorname{tr}\left[\left(V-V^{*} Q\right) W\left(V-V^{*} Q\right)^{\mathrm{T}}\right]
\end{aligned}
$$

is the Truth Discorvery term

The $V^{*}$ is vector of the final output "truth", $Q$ simply extends the vector to a matrix of same columns, $W$ is an unknown weight matrix.

## Algorithm

Similar to previous: gradient descent

## Discussion

**What is the insight of doing this?**

The matrix $V$ in factorization is the "virtual users" whose linear combination is assumed to yield the matrix $X$. Then the correlation term and the truth discovery term finds the truth among these "virtual users"

**Is the performance better than previous methods?**

**The solution for Regularized PCA is the PCA whose singluar value is greater than a threshold? What about the $V$ in this problem** 

## Reference

C. Meng, W. Jiang, Y. Li, J. Gao, Lu Su, H. Ding, Y. Cheng, “Truth Discovery on Crowd Sensing of Correlated Entities”, in SenSys 2015. 