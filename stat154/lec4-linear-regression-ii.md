---
description: multiple linear regression
---

# lec4 Linear Regression II

## Parameter estimation

$$\text{RSS}(\beta) = \sum_{i=1}^n e_i^2 = \sum_{i=1}^n(y_i - x_i^T \beta)^2=||y-X\beta||^2_2$$
$$\nabla_{\beta}\text{RSS}(\beta) = 2X^T(y -X\beta)=0\Rightarrow \hat{\beta} = (X^TX)^{-1}X^Ty \in \mathbb{R}^{d+1}$$

## Confidence interval

$$\hat{\beta} - \beta \sim \mathcal{N}(0, (X^TX)^{-1}\sigma^2)$$

$$\hat{\beta} -\beta =  (X^TX)^{-1}X^T(X\beta + \epsilon) -\beta =(X^TX)^{-1}X^T \epsilon$$

$$E[\hat{\beta}-\beta] = 0$$
$$\operatorname{Var}(\hat{\beta}) = (X^TX)^{-1}X^T(\sigma^2 I)X(X^TX)^{-1}=(X^TX)^{-1}\sigma^2$$

$$\text{SE}(\hat{\beta_j})=\sqrt{(X^TX)_{jj}^{-1}}\sigma, j = 0,1,\dots,d$$

$$I_j = [\hat{\beta_j}-t_{\alpha}\text{SE}(\hat{\beta_j}),\hat{\beta_j}+t_{\alpha}\text{SE}(\hat{\beta_j})]$$
$$t_{\alpha}$$ is such that $$P(\beta_j \in I_j)=1-\alpha$$

![fig1](images/stat154lec4fig1.png)

## Hypothesis testing

