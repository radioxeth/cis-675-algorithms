# Week 2: The Master Method, Divide and Conquer, Sorting

## 2.1 Weekly Introduction
### Contents
- Recurrence relations
- The master method for solving recurrence relations
- Divide-and-conquer algorithms
- Sorting

## 2.2 Exercise: Recurrence Relations
- **recurrence relation** is an euqation that recursively defines a function's values in terms of earlier values
- It can be very useful for analyzing an algorithm's running time!

### Recurrence relations in math
- Fibonacci numbers
  - `f(1)=1`
  - `f(2)=1`
  - `f(n)=f(n-1) + f(n-2)`

### Recurrence relations in code

```
def naivePower(x,n):
  if n==0:
   return 1                           #c1
  else:
   return x*naivePower(x,n-1)         #c2+T(n-1)
```
> How can we write the running time?
$T(n)=c1$
$T(n)=c2+T(n-1)$
*came naturally from the code*

If only we had an expression for $T(n-1)$
Expanded:
> $T(n)=c2+T(n-1)$
$=c2+c2+T(n-2)$
$=c2+c2+c2+T(n-3)$
$=c2+...+c2+T(0)=c2+...+c2+c1$
$nc2+c1$
*simplified to function*

### Recurrence relations in code
```
def betterPower(x,n):
    if(n==0):
        return 1               #c1
    else if(n==1):
        return x               #c2
    else:
        return Power(x*x,n/2)  #c3+T(n/2)
```
*assume for simplicity that n is a power of 2*
How can we write the running time?

> `Power(x*x,n/2)` $(x^{2})^{n/2}=x^{n}$
$T(0)=c_1$
$T(1)=c_2$
$T(n)=c_3+T(n/2)$
(for simplicity we'll assume n is a power of 2)

If only we had an expression for $T(n/2)$...
Expanded:
>$T(n)=c_3+T(n/2)$
$=c_3+c_3+T(n/4)$
$=c_3+c_3+c_3+T(n/8)$
$=kc_3+T(n/(2^{k}))$ *what should k be in order for us to get down to T(1)?*
$k=log_2(n)$
$=log_2(n)c_3+T(1)=c_3log_2(n)+c_2$

### Writting functions as recurrences
- many "normal" mathematical functions can be written as recurrence relations:
- $f(x)=x$
  - $f(x)=1+f(x-1), f(0)=0$
- $f(x)=2^x$
  - $f(x)=2*f(x-1),f(0)=1$
- $f(x)=x!$
  - $f(x)=x*f(x-1),f(1)=1$

### Solving recurrences
- Solving recurrence relations is like integrating an equation - there are tricks, but no tequniques are guaranteed to work.
- Simplest method: Guess the solution; prove with induction.
- Sometimes it helps to do a few expansions to get some intuition.

#### Example
> *Claim*: The recurrence relation given by:
$T(0)=c_1$ *naive power*
$T(n)=c_2+T(n-1)$
has the solution $T(n)=nc_2+c_1$

> *Proof*: Proof by induction. Base case: $n=0$. $T(0)=c_1, nc_2+c_1=0c_2+c_1=c_1$
Assume for some n, that $T(n)=nc_2+c_1$.
Show for $n+1$.
$T(n+1)=c_2+T(n)=(n+1)c_2+c_1$, which is what we wanted. &square;

> There's something I think I'm missing here. Hopefully seeing the answers will help me make a connection somewhere
> 1. $2^n-n$
> 2. 
> 3. n!
> 4. $n$
> 

## 2.3 The Master Method
Suppose $T(n)=aT(\lceil\frac{n}{b}\rceil)+O(n^d)$
> $a$ controls the number of sub problems
> $b$ tells you how big the sub problems are
> $O(n^d)$ is extra work inside recurrence call

- Case 1: if $d>log_b(a)$, then $T(n)=O(n^d)$
- Case 2: if $d=log_b(a)$, then $T(n)=O(n^d log(n))$
- Case 2: if $d<log_b(a)$, then $T(n)=O(n^{log_b(n)})$


#### example
Binary Search pseudo code

```
binary_search(array,value,low,high):
  middle=(low+high)/2          c1
  if(array[middle]===value)
    return middle              c2
  else if(array[middle]<value) 
    return binary_search(array,value,middle,high) c3+n/2
  else(array[middle]>value)
    return binary_search(array,value,low, middle) c3+n/2
```

$T(n)=c_1+c_2+c_3\frac{n}{2}+c_3\frac{n}{2}$
$T(n)=T(\frac{n}{2})+c_1$
- a=1
- b=2
- d=0

$log_2(1)=0$
$T(n)=O(n^0log(n))=O(log(n))$

## 2.4 Divide and Conquer

### Overview
1. Break the problem into smaller problems
2. Recursively solve the problems
3. Combine the subproblem solutions to solve the original problem

#### Multiplication
- How do we do binary multiplication?
> `n` = # of bits in the numbers
>  101101
> x010011

- What is the running time of this method
> O(n^2)
- Can we do better?

#### Multiplication v3

- complex number multiplication:

$(a+bi)(c+di)=ac-bd+(bc+ad)i$
> 4 multiplicaitons

OR

$(a+bi)(c+di)=ac-bd+((a+b)(c+d)-ac-bd)i$
> 3 distinct multiplications


#### 2.4.2
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

### MergeSort
- Given an input array of real numbers, we want to output the array in sorted order
- Merge sort:
  - split the array in half
  - sort each half
  - merge the two halves together

**Merge sort**
```
a[1...n] mergeSort(a[1...n]){
  if(n>1):
    return merge(mergesort(a[1...n/2]),mergesort(a[[n/2]+1...n]))
  else:
    return a
}
```
**Merge**
```
function merge(x[1...k],y[1...l])
if(k==0) return y[1..l]
if(l==0) return x[1..k]
if(x[1]<y[1]):
 return x[1] concat merge(x[2..k],y[1..l])
else:
 return y[1] concat merge(x[1..k],y[2..l])
```
N=k+l
T(N)=c+T(N-1)=Nc=O(N)
T(1)=c

#### 2.4.6 Exercise
What is the running time of mergesort?

> $a$: 2 subproblems mergesort left-and mergesort-right
> $b$: 2 $n/2$ is size of subproblems
> $d$: 1 merge is $O(n)$
> $T(n)=2T(\frac{n}{2})+O(n^1)$
> using the master method... $d ? log_b(a)$...$1=log_2(2)$
> $O(n^dlog(n))...O(nlog(n))$


### Matrix Multiplication

$Z_{ij}=\displaystyle\sum_{k=1}^{n}X_{ik}Y_{kj}$
$O(n^2)*n^2=O(n^3)$

*Volker Strassen*

### Median
- How do we find the median of an array?

- Sort the array; pick the midpoint

- what is the running time of this?
$O(nlogn)$
- But sorting does a lot of extra work - can we do better?

- How do we find the kth smallest element?

#### Exercise 2.4.11
*Daniel Shannon*

> We can compare the value k to the lengths of the arrays.
> if $k \le size(S_L)$, $k_{th}$ smallest value is in $S_L$
> if $size(S_L) \lt k  \le (size(S_L)+size(S_V))$, $k_{th}$ smallest value is in $S_V$
> if $size(S_L)+size(S_V) \lt k  $, $k_{th}$ smallest value is in $S_R$

#### Exercise 2.4.13
*Daniel Shannon*

What is the wost-case running time of this method? Hint think about the size of the subproblem.

> The worst case running time of the method would be. Assuming one sub array equal to length of the array and a merge sort...
> $T(n)=3T(\frac{n}{1})+O(n)*O(nlogn)$
> using the master method...
> d=2
> a=3
> b=1
> $d?log_b(a)$...$2=log_2(4)$
> $O(n)=n^2log(n)$

> This could happen if the value $v$ is either the largest or the smallest value of the array.

#### Exercise 2.4.15
*Daniel Shannon*

If you pick a good v by how much will the array shrink?
> The array on average will shrink to a size of $\frac{n}{2}$.
> You would have to pick a value, $v$, $\frac{n}{2}$ times for it to be *good*.

**running time as a recurrence**
a=1
b= 4/5//every 2 iterations, shrinking by 25%, $S' \le \frac{3}{4}S=\frac{S}{4/3}$
d= 1


## 2.5 Sorting

Goal: sort an array
- Worst case running time? When does this happen>
- Average case running time?
- How much space required?
- How many writes required? Frequency of cache misses?
- Which situations is it best suited for?

#### Exercise 2.5.2
*Daniel Shannon*
```C
void bubbleSort(int arr[], int n)
{
    for (int i = 0; i < n - 1; i++)
    {
        for (int j = 0; j < n - i - 1; j++)
        {
            if (arr[j] > arr[j + 1])
            {
                swap(arr[j], arr[j + 1]);
            }
        }
    }
}
```
> $T(n)=1T(\frac{n}{1})+O(n^2)$
> using the master method...
> a=1
> b=1
> d=2
> $d?log_b(a)...2>log_1(1)...O(n^2)$
> Worst case running time is $O(n^2)$ - this happens when the array is in reverse order!

#### Exercise 2.5.4
*Daniel Shannon*
> Insertion sort will still have a worst-case running time of $O(n^2)$ because if the array is in reverse order, we will still have to run this for every n twice.
> Additionally, this will require n extra space because to shift we need n-space to shift the sorted array. 

#### Exercise 2.5.6
*Daniel Shannon*
> The running time of insertion sort is $O(n^2)$ and the worst case is sorting in reverse order.

#### Exercise 2.5.8
*Daniel Shannon*
> The cost to split an array would be $O(n)$ and the size of the sub arrays is $O(\frac{n}{2}$),

#### Exercise 2.5.10
*Daniel Shannon*
> There would be $n!$ leaf nodes.
> For a binary tree, the minimum depth would be $O(nlog(n))$.
