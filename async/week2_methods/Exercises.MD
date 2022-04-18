#### 2.4.2 Exercise
*Daniel Shannon*

$xy=2^n x_L y_L + 2^{(n/2)}(x_L y_R+x_R y_L)+x_R y_R$
> $a$: 4 subproblems
> $b$: 2 ($n/2$)
> $d$: 1 addition and shifting is easy
> $T(n)=4T(\frac{n}{2})+O(n)$
> ... using the master method $d?log_b(a)$...$1<log_2(4)$...$1<2$ 
> $O(n^2)$

#### 2.4.4 Exercise
*Daniel Shannon*

$xy=2^n x_L y_L + 2^{(n/2)}(x_L y_R+x_R y_L)+x_R y_R$
$x_Ly_R+x_Ry_L=(x_L+x_R)(y_L+y_R)-x_Ly_L-x_Ry_R$
...
$xy=2^n x_L y_L + 2^{(n/2)}((x_L+x_R)(y_L+y_R)-x_Ly_L-x_Ry_R)+x_R y_R$
> $a$: 3 subproblems
> $b$: 2 ($n/2$)
> $d$: 1 adding and shifting is $O(n)$
> $T(n)=3T(\frac{n}{2})+O(n)$
> ... using the master method $d?log_b(a)$...$1<log_2(3)$...$log_2(3)$ 
> $O(n^{log_2(3)}) ... O(n^{1.59})$

#### 2.4.6 Exercise
*Daniel Shannon*
What is the running time of mergesort?

> $a$: 2 subproblems mergesort left-and mergesort-right
> $b$: 2 $n/2$ is size of subproblems
> $d$: 1 merge is $O(n)$
> $T(n)=2T(\frac{n}{2})+O(n^1)$
> using the master method... $d ? log_b(a)$...$1=log_2(2)$
> $O(n^dlog(n))...O(nlog(n))$

