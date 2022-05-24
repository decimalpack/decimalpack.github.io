# Recurrence Relation - Cookbook

## Extended Master's Theorem for Divide and Conquer [^master-theorem-baeldung] [^advanced-masters-divide-and-conquer]


$$
T(n) = a T(n/b) + \Theta(n^k \log^p n)
$$

Where,

$$
\begin{aligned}
  a & \ge 1 \\
  b & > 1 \\
  k & \ge 0 \\
  p & \in Real
\end{aligned}
$$


1. If $a > b^k$, then $T(n) = \Theta(n^{\log_b a})$
2. If $a = b^k$, then
    1. if $p > -1$, then $T(n) = \Theta(n^{\log_b a} \log^{p+1}n)$
    2. if $p = -1$, then $T(n) = \Theta(n^{log_b a} \log\log n)$
    3. if $p < -1$, then $T(n) = \Theta(n^{\log_b a})$
  
3. If $a < b^k$, then
    1. if $p \ge 0$, then $T(n) = \Theta(n^k \log^pn)$
    2. if $p < 0$, then $T(n) = \Theta(n^k)$

### Change of Variables [^2]

We can apply Master's theorem on recurrences like:

$$
T(n) = T(\sqrt{n}) + 2
$$


$$
\therefore T(2^n) = T(2^{n/2}) + 2
$$


$$
\text{Let} \ S(m) = T(2^m)
$$


$$
\therefore S(m) = S(m/2) + 2
$$

After applying Master's theorem, we get $S(m) = \Theta(\log_2(m))$
That is,

$$
T(2^m) = \Theta(\log_2(m))
$$

Put $m \rightarrow \log_2(n)$

$$
T(2^{\log_2(n)}) = \Theta(\log_2(\log_2(n))) 
$$


$$
T(n) = \Theta(\log_2(\log_2(n))) 
$$


## Master Theorem For Subtract and Conquer Recurrences [^master-theorem-subtract-and-conquer]

Solves recurrences of the form

$$
T(n) = a \cdot T(n-b)+\Theta(n^k)
$$

for some constants $c, \ a>0, \ b>0, \ k \ge 0$

1. If a<1 then $T(n) = \Theta(n^k)$
2. If a=1 then $T(n) = \Theta(n^{k+1})$
3. if a>1 then $T(n) = \Theta(n^ka^{n/b})$

## Akra-Bazzi Method

Read [this article](https://www.baeldung.com/cs/akra-bazzi) first.


Can solve equations of form. See [Wikipedia-Formulation](https://en.wikipedia.org/wiki/Akra–Bazzi_method#Formulation)

$$
T(x)=g(x)+\sum _{{i=1}}^{k}a_{i}T(b_{i}x+h_{i}(x))\qquad {\text{for }}x\geq x_{0}.
$$

!!! note
    $0 < b < 1$, hence cannot be applied for equations like $T(n) = T(n-1) + 1$

This method applies to a very wide variety of divide-and-conquer equations!

## References

[^master-theorem-baeldung]: <https://www.baeldung.com/cs/master-theorem-asymptotic-analysis>
[^2]: http://iiitdm.ac.in/old/Faculty_Teaching/Sadagopan/pdf/DAA/new/recurrence-relations-V3.pdf
[^master-theorem-subtract-and-conquer]: https://www.geeksforgeeks.org/master-theorem-subtract-conquer-recurrences/
[^advanced-masters-divide-and-conquer]: https://www.geeksforgeeks.org/advanced-master-theorem-for-divide-and-conquer-recurrences/
