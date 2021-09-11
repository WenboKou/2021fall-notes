# Matrices

## Matrix-vector product

Let $$A \in \mathcal{R}^{m,n}$$ be a matrix with columns $$a_1, \dots, a_n \in \mathcal{R}^m$$
and $$b\in R^{n}$$ a vector. We define the matrix-vector product by
$$Ab = \sum_{k=1}^n a_k b_k$$

Similarly, we can multiply matrix $$A\in R^{m,n}$$ on the left by (the transpose of) vector $$c\in \mathcal{R}^m$$ as follows
$$c^T A = \sum_{k=1}^m c_k \alpha_k^T, A\in \mathcal{R}^{m,n},c\in \mathcal{R}^{m}$$.
Though it's not easy to see why this is the case, we can derive this as follows:
$$A^Tc = \sum_{k=1}^m c_k\alpha_k \Rightarrow c^T A = \sum_{k=1}^m c_k \alpha_k^T$$