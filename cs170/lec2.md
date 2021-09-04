# lec2

## 1. More Arithmetic

Algorithms for computing: Fibonacci numbers.$$F_0 = 0, F_1 = 1,\dots ,F_n = F_{n-1} + F_{n-2}, n > 1$$. Design algorithm to compute Fibonacci numbers. _Flop_ = Floating Point Operation: addition, subtraction, multiplication, division.

### 1. Alg 1: Recursion

```text
def FibRec(n):
    if n <= 1: return n
    else: return FibRec(n-1) + FibRec(n-2)
```
Addition is the only flop in this algorithm.
Let $$T(n)=$$ #flops to compute $$F_n$$.
$$T(n)=\begin{cases}
    0, n\leq 1\\
    T(n-1) + T(n-2) + 1, n > 1
\end{cases}$$
$$F_n = F_{n-1} + F_{n-2} \geq 2\cdot F_{n-2} \geq 2^2\cdot F_{n-2\cdot2} \geq 2^{\frac{n}{2}}$$. For the same reason $$F_n \leq 2^n$$. So the number of flops is exponential.

### 2. Alg 2: Iteration

```text
def FibIter(n):
    if n <= 1: return n
    a  = 0
    b = 1
    for i = 1 to n - 1:
        tmp = b
        b = a + b
        a = tmp
    return b
```
Addition is the only flop. And number of flops is $$\Theta(n)$$.

### 3. Alg 3: Fast Matrix Powering

$$
\begin{bmatrix}
    1 & 1\\
    1 & 0
\end{bmatrix} \begin{bmatrix}
    F_n \\
    F_{n-1}
\end{bmatrix} = \begin{bmatrix}
    F_{n+1} \\
    F_n
\end{bmatrix}
$$
So $$\begin{bmatrix}F_{n+1}\\
    F_n\end{bmatrix} = A^n\begin{bmatrix}1 \\0 \end{bmatrix}$$

For example we want to compute $$9^{71}$$.
$$9^1, 9^2, 9^4, 9^8, 9^{16}, 9^{32}, 9^{64}$$
$$71 = 64 + 4 + 2 + 1$$.
Total need $$<= 2 \cdot \log_2{n}$$ flops. Because we need $$\log_2{n}$$ times multiplication and at most need  $$\log_2{n}$$ times addition to get the final result.


## 2. Asymptotic Notation
## 3. Preview of next topic(Divide and Conquer)
