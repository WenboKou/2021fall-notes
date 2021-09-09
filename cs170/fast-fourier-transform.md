# lec4 Fast Fourier Transform

## 1.polynomial multiplication
$$A(x)=a_0 + a_1x + \dots + a_{d-1}x^{d-1}$$
$$B(x)=b_0 + b_1x + \dots + b_{d-1}x^{d-1}$$
$$C(x)=c_0 + c_1x + \dots + c_{2d-2}x^{2d-2}$$.
Treat all of $$A,B,C$$ as polynomial degree $$< N$$(can pad $$A,B$$ with 0 coefficients.)
### Relationship between polynomial and int multiplication
Given integer $$\alpha, \beta $$ want to calculate $$\gamma = \alpha * \beta$$,$$\alpha = \alpha_{N-1}\alpha_{N-2}
\alpha_{N-3}\dots
\alpha_0$$,
$$\beta = \beta_{N-1}\beta_{N-2}
\beta_{N-3}\dots
\beta_0$$
$$A(x)=\alpha_0 + \alpha_1x + \dots + \alpha_{N-1}x^{N-1}\Rightarrow \alpha = A(10)$$
$$B(x)=\beta_0 + \beta_1x + \dots + \beta_{N-1}x^{N-1} \Rightarrow \beta = B(10)$$
So we can compute $$\gamma = \alpha \beta = (AB)(10)$$  

## 2.Fast Fourier Transform

## 3.Cross-correlation

