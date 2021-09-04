# lec2

## 1. More Arithmetic

Algorithms for computing: Fibonacci numbers.$$F_0 = 0, F_1 = 1,\dots ,F_n = F_{n-1} + F_{n-2}, n > 1$$. Design algorithm to compute Fibonacci numbers. _Flop_ = Floating Point Operation: addition, subtraction, multiplication, division.

### 1. Alg 1:

```text
def FibRec(n):
    if n <= 1: return n
    else: return FibRec(n-1) + FibRec(n-2)
```

Addition is the only flop in this algorithm. Let $$T(n)=$$ \#flops to compute $$F_n$$. $$T(n)=\begin{cases} 0, n\leq 1\\ T(n-1) + T(n-2) + 1, n > 1 \end{cases}$$

## 2. Asymptotic Notation

## 3. Preview of next topic\(Divide and Conquer\)

