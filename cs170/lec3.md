# lec3 Divide-and-Conquer \(Part II\)

## Divide and Conquer
Idea: Divide the input into smaller parts, recurse on parts and combine.
### 1. Matrix multiplication
$$A_{n\times n} B_{n\times n}  = C$$
$$C_{ij}=\sum_{k}A_{ik}B_{kj}$$
Natural implementation is 3 nested for loops each with iteration. $$\Theta(n^3)$$ flops. Let's improve this algorithm.

### 2. Sorting(MergeSort)
Divide array in half and recursively merge each half array and merge the two array.
```text
def MS(A[1 ... n]):
    B <- MS(A[1 ... n/2])
    C <- MS(A[n/2+1 ... n])
    return Merge(B, C)
```
![Merge](images/cs170lec3fig2.jpg)
$$T(n) = 2T(\frac{n}{2}) + c \cdot n = \Theta(n\log n)$$.

#### 1. Iterative MergeSort
```text
Queue Q
While Q.size() > 1:
    pop off the first two lists,
    merge them and push back onto Q.
```
![iterative mergesort](images/cs170lec3fig3.jpg)
In phrase $$j$$, each list has size $$2^j$$, at the end $$j=\log 2$$. And in each phrase it takes $$\Theta(n)$$, so the total runtime is $$n\Theta(n)$$.

#### 2. Proof
will show $$\Omega(n\log n)$$ comparisons needed even if promised $$A$$ is some Permutation of $${1, ..., n}$$. 

![还是不知道这是怎么证明的](images/cs170lec3fig4.jpg)

$$n! = 1 \cdot 2 \cdot ... \cdot \frac{n}{2} + 1 \cdot ... \cdot n \leq n^n$$

$$\log(\frac{n}{2})^{\frac{n}{2}} \leq \log (n!) \leq \log(n^n)$$. So $$\log n! = \Theta(n\log n)$$

### 3. Selection/Median
Return the k-th smallest/middle element in the array.

Can assume all elements of A are distinct.(Replace A[i] with (A[i], i), do lex comparison.)

#### 1. QuickSelect(A, k)

```text
Pick median of A p(suppose known)
Scan all elements small than p go to left[Total L elements], greater than p go to right[Total R elements].
if k = |L| + 1: return p
elif: k <= |L|, return QS(L, k)
else: return QS(R, k)
Do recursion.

``` 

