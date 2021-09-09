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

### Alg1: "straight forward"

$$c_k = \sum_{j=0}^k a_jb{k-j}$$
```text
loop over i = 0 to N - 1
    compute c: loop j = 0 to i
```
total runtime is $$\mathcal O(N^2)$$

### Alg2: Karatsuba

see figure1

### Polynomial Interpolation

A degree $$< N$$ polynomial is fully determined by its evaluation on $$N$$ distinct points.  
* Rather than obtain the coefficients of C directly by multiply AB, we will determine $$C(x_0),C(x_1),\dots,C(x_{N-1})$$ for distinct $$x_i$$.
* Compute evaluation of $$A,B$$ on N distinct points each, multiply them, then interpolate to get back the coefficients from the evaluations of C. 
  
### Why does interpolation work?
see fig2 

## 2.Fast Fourier Transform

### The Discrete Fourier Transform(DFT) is a matrix

complex number recap: $$z = a + \sqrt{-1}b=re^{\sqrt{-1}\theta}$$
fig3

A DFT matrix $$F$$
$$F_{ij}=(\omega)^{ij}=(e^{\frac{2\pi \sqrt{-1}}{N}})^{ij}$$

fig4

### The Fast Fourier Transform(FFT) is an algorithm

* an algorithm for quickly computing $$p(1),p(\omega),\dots,p(\omega^{N-1})$$ for some degree < N polynomial p. In other words, adjusting DFT to vector of p's coefficients.
$$p(z)=p_0 + p_1 z + p_2 z^2 + \dots + p_{N-1}z^{N-1}=p_0+p_2z^2 + \dots + p_{N-2}z^{N-2} + z(p_1 + p_3z^2 + p5z^4 + \dots) = p_{\text{even}}(z^2) + zp_{\text{odd}}(z^2)$$
$$T(N)=2T(\frac{N}{2})+\Theta(N)=\Theta(N\log N)$$

### Poly mult alg
```text
given coefficients of A(x) and B(x)
use FFT to compute a' = Fa(a is coeff vector of A)
use FFT to compute b' = Fb
for i = 0 to N - 1:
    compute ci' = a'ib'i(c' is the evaluation of C(x) on 1, omega,...,omega^{N-1})
c = F^{-1}c'
return c(coeff vector of C = AB)   
```
Total:$$\mathcal{O}(N\log N)$$ assuming we can mult/add complex numbers in constant time.

### Claims:

1.fig5
2.$$\bar{M}x = \bar{M\bar{x}}\Rightarrow F^{-1}\hat{c} = \frac{1}{N}\bar{F\bar{\hat{c}}}$$

## 3.Cross-correlation
fig6
