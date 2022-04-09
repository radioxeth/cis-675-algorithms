# Week 1 Proof Techniques, Asymptotic Analysis, and Recurrence Relations

## 1.1 Weekly Introduction
- Review of proof techniques (including induction)
- Review of running time analysis, including big-O notation, recurrence relations, and the master theorem

## 1.2 Course Introduction

### Course Topics
- Analyzing running time of algorithms
  - Big-O analysis
  - Recurrence relations
- Designing algorithms
  - Divide and conquer
  - Greedy algorithms
  - Dynamic programming
  - Linear programming
- Complexity classes
  - P vs NP
  - Reducitons and NP-completeness

## 1.3 Self Introduction

## 1.4 Proof Techniques

### Proofs

### How to Write a Proof

> Is the sum of two even numbers even, odd, or possibly either?

> *Claim*: The sum of two even numbers is even.
> *Proof*: An even number `n` can be written as `n = 2k` where `k` is an integer.
> Let `u`,`v` be even numbers. `u = 2k1`, and `v=2k2`, so `u + v = 2k1 + 2k2 = 2(k1 + k2)`
> `k1 + k2` is an integer, so `u + v` is even. &square;

### Proving a Mathematical Claim
- There are several ways to prove a claim
  - Direct proof
  - Proof by contradiction
  - Proof by induction
  - Proof by examples
  - Others!
- Always clearly state what you are trying to prove.

### Direct Proof
- Combine axioms, theorems, facts, etc to reach the claim
> Example: Prove that the product of two even integers is even

> *Claim*: The product of two even integers is even
> *Proof*: Let `u`,`v` be even integers. Then `u=2k1`,`v=2k2`, so `u*v = 4*k1*k2`
> = `2(2k1*k2)`, `2k1k2` is an integer, so `uv` is even. &square;

#### Example Problem 1.4.2

> Prove that if `n` is even, <code>(-1)<sup>n</sup> = 1</code>

**My Answer**
> *Claim*: <code>(-1)<sup>n</sup></code> is `1` when `n` is even
> *Proof*: Let `n` be an even integer, `2k`. <code>(-1)<sup>n</sup> = (-1)<sup>2k</sup></code>. Then <code>(-1)<sup>2</sup>=1</code>, so <code>1<sup>k</sup>=1</code>, for `k>0` &square;

**Prof's Answer**
> *Claim*: <code>(-1)<sup>n</sup></code> is `1` when `n` is even
> *Proof*: Let `n` be an even integer, `2k`. <code>(-1)<sup>n</sup> = (-1)<sup>2k</sup></code>. Then <code>((-1)<sup>2</sup>)<sup>k</sup>=1<sup>k</sup></code>, so <code>1<sup>k</sup>=1</code>, for `k>0` &square;


### Proof by Contradiction
- Show that if the claim were not true, something impossible occurs
- Example: Show that there is no largest prime number

> *Claim*: There is no largest prime number
> *Proof*: Suppose for a contradiciton that there is a largest prime number <code>p<sub>n</sub></code>
> Let <code>p<sub>1</sub></code>...<code>p<sub>n</sub></code> be all prime numbers. Define `q`= the product of <code>p<sub>1</sub></code>...<code>p<sub>n</sub> &plus; 1</code>. `q` is not divisible by <code>p<sub>1</sub></code>...<code>p<sub>n</sub></code>. From *prime factorization theorem* (PFT), `q` is prime or a prime was left out of the list. Contradiction, so there cannot be a largest prime. &square;

#### Example Problem 1.4.4
> Show that there is no smallest positive rational number.
`r=p/q` `p`&`q` are integers.


**My Answer**
> *Claim*: There is no smallest positive rational number
> *Proof*: Suppose for a contradiction that there is a smallest postive rational number, <code>r<sub>n</sub>=p<sub>n</sub>/q<sub>n</sub></code> with <code>q<sub>n</sub>...q<sub>n+1</sub></code>. <code>r<sub>n+1</sub>=p<sub>n+1<sub>q<sub>n+1</sub></code> would be not smaller than <code>q<sub>n</sub></code>. Contradiction, as q<sub>n+1</sub> is a smaller rational number than <code>q<sub>n</sub></code>

**Prof's Answer**
> *Claim*: There is no smallest rational number
> *Proof*: Suppose for a contradiction that that there is a smallest rational number, call it `r`. Define `r2=r/2`. `r2` &lt; `r`, but `r2` is rational. `r=p/q`, `r2=p/2q`, where `p`&`q` are integers. Contradiction.


### Proof by Induction
- Prove that the "base case" is true (usually P(1)).
- Assume that P(N) is true.
- Assume that P(N+1) is true.

> Similar to recursion. Show that recursion will work with smallest N, then assume it works for other values of N


### Example
> Prove that for any positive integer `n`, `1+2+...+n=n(n+1)/2`

> *Claim*: For any positivite integer n
*Proof*: By induction. Base case: Let `n=1`. Then `1 = 1(1+1)/2 = 1`. Assume that the claim holds for some `n`. We will show it holds for `n+1`.
> From IH: `1+2+...+n = n(n+1)/1`. `1+2+...+n = (n(n+1)/2)+n+1 = (n+1)(n+2)/2`, so claim holds &square;


#### Example Problem 1.4.6

#### My Answer
> Prove that for any integer `n`&ge;`1`, <code>2<sup>1</sup> + 2<sup>2</sup> + 2<sup>3</sup> +...+ 2<sup>n</sup>=2<sup>n+1</sup>-2</code>
> *Claim*: For `n`&ge;`1`, <code>2<sup>1</sup> + 2<sup>2</sup> + 2<sup>3</sup> +...+ 2<sup>n</sup> = 2<sup>n+1</sup>-2</code>
> *Proof*: By induction. Base case: Let `n=1`. Then <code>2<sup>1</sup> = 2<sup>2</sup>-2 = 4-2 = 2</code>. Assume that the claim holds for some `n`. We will show that it holds for `n+1`.
> From IH: <code>2<sup>1</sup> + 2<sup>n+1</sup> = 2<sup>n+1+1</sup>-2</code>
> <code>2<sup>1</sup> + 2<sup>n</sup>2<sup>1</sup> = 2<sup>n</sup>2<sup>2</sup>-2</code>
> <code>1 + 2<sup>n</sup> = 2<sup>n+1</sup>-1</code>
> <code>2<sup>n</sup> = 2<sup>n+1</sup>-2</code> &square;

#### Prof's Answer
> *Claim*: For `n`&ge;`1`, <code>2<sup>1</sup> + 2<sup>2</sup> + 2<sup>3</sup> +...+ 2<sup>n</sup> = 2<sup>n+1</sup>-2</code>
> *Proof*: By induction. Base case: Let `n=1`. Then <code>2<sup>1</sup> = 2<sup>2</sup>-2 = 4-2 = 2</code>. Assume that the claim holds for some `n`. We will show that it holds for `n+1`.


### Proof By Example
- If you need to show that something is possibl (as opposed to always true or always false), then give an example.

#### Example
> Prove that there is exists a positive integer greater than 5 that is divisible bby 3.

#### 1.4.8

> Is the following statement true or false. Prove your answer. Every integer larger than 10 is even.

> *Claim*: Every integer larger than 10 is even is false.
> *Proof*: 11 is and an integer greater than 10. 11%2 != 0 and is odd. So this is false. &square;

- If you need to show that something is possible (as opposed to always true or always false), then give and example
- Giving an example is only sufficient when you need to show that something is not possible! Not sufficient in general.


## 1.5 Running Time Analysis

### Why Analyze Running Time?
- Suppose you've created a new algorithm
- How do you convince people to use it
- Does it...
  - run faster?
  - use fewer resources?
- Suppose I've invented a new sorting algorithm **SUSort**
- How do I show that it beats exisiting methods?
- Easiest way:
  - Make up a bunch of test cases
  - Run SUSort and other sort alogrithms on those test cases
  - Which finishes first?


> How do we know they're the "right" test cases
> Computers get faster; Data gets bigger - will the ordering change next year?

- *Data sizes are doubling* every year!
- Moore's law: Density of transistors doubles every 18-24 months: *more processing speed!* (Through this rate of increate is starting to be reduced)
- If your program takes 2 minutes to run today, how long will it take next year.

### Key Observations
- Run-time analysis should be:
  - independent of the **platform**
  - independent of the **programmer's skill**
  - independent of **specific test cases** (content and size)
  - Theoretically rigorous

### How can we do better?
- **Theoretical analysis of algorithms** is used to estimate the run-time of an algorithm as a function of the size of the input
- This run-time is given in terms of the number of **primitive operations** required (eg arithmetic operations)

```
Run time = 5 seconds <- depends on input and machine setup, compiler...
vs
Run time = 5,000 primitive operations <- depends on input content and size
vs
Run time = 500n, where n is length of specific type of input <- depends on input content
vs
Worst-case run time = 900n, where n is length of input <- the right way to do it
```

#### Example
```python
function sumArray(arr)
  tot_sum = 0                                 # c1
  tot_product_sum =0                          # c1
  for idx in range(len(arr)):                 # N
    tot_sum += arr[idx]                       # c2
  for idx1 in range(len(arr)):                # N
    for idx2 in range(len(arr)):              # N
      tot_product_sum += arr[idx1]*arr[idx2]  # c3
  return tot_sum, tot_product_sum             # c4

# 2c1 + Nc2 + N^2c3 + c4
```

### Big-O Notation: Definition

> **MEMORIZE THIS**
>
> `f(x)=O(g(x))`
> - There exists:
>   - some positive constant M
>   - some minimum x-value x<sub>0</sub>
> - Such that for all x&gt;x<sub>0</sub>:
>   - <code>f(x) &le; M * g(x)</code>


<code>
f(x)=x<sup>2</sup>;
g(x)=(1/2)x<sup>2</sup>;
f(x)=O(g(x));
M=3;
x<sub>0</sub>=1;
x<sup>2</sup> &le; (3/2)x<sup>2</sup>;
f(x)&le;3g(x) for all x&gt;1;
</code>

> O(g(x)) is a set
> When we say f(x)=O(g(x)), we mean f(x)&isin;O(g(x))

### Big-O Notation: Notation Conventions
- O(g(x)) represents a set, so the = sign doesn't mean what it normally means
- We use "=" to represent **set membership**
- This means that "equality" is **not symmetric**

> we can say `f(x)=O(g(x))` but not `O(g(x))=f(x)`
> `f(x)&isin;O(g(x))`


#### Big-O Notation: Example
```python
function sumArray(arr)
  tot_sum = 0                                 # c1
  tot_product_sum =0                          # c1
  for idx in range(len(arr)):                 # N
    tot_sum += arr[idx]                       # c2
  for idx1 in range(len(arr)):                # N
    for idx2 in range(len(arr)):              # N
      tot_product_sum += arr[idx1]*arr[idx2]  # c3
  return tot_sum, tot_product_sum             # c4

# 2c1 + Nc2 + N^2c3 + c4
# c values are hardware dependent
# reduces to
# g(N)=N^2
# O(N^2), captures the essence of the running time
```

### Other types of Asymptotic Relationships

### Little-o notation defintion
> `f(x)=o(g(x))` iff:
> - for every postitive &epsilon;,
>   - there exists a constant x<sub>&epsilon;</sub>
>   - such that <code>f(x)&le;&epsilon;g(x)</code> for all <code>x&ge;x<sub>&epsilon;</sub></code>

> <code>&darr;&epsilon; ... f(x)&le;&epsilon;g(x)</code>

> *Informally, this means that g(x) grows much faster than f(x): for EVERY &epsilon;, no matter how small, we can find a place where g(x) is 1/&epsilon; times bigger than f(x). In other words, even if we shrink g(x) by a factor of 100, 1,000, 1,000,000 ... it is still going to be bigger than f(x)*


### Exercises
#### 1.5.2
> Q: What is the key difference between big-O and little-o relationship?

> The key difference between the big-O and little-o relationship is in regards to how the definitions hold true with respect to x. Big-O holds true for a certain constant, M for values greater than x<sub>0</sub>. Little-o holds true for all values of <code>x&ge;x<sub>&epsilon;</sub></code>, no matter how big or small &epsilon; is. In big-O the constant matters, but not with little-o.

> **prof's answer** If `f(x)=o(g(x))`, it is also `O(g(x))`. But if `f(x)=O(g(x))`, it is not necessarily `o(g(x))`!
> <code>f(x)=x^2 g(x)=x^3 x<sub>&epsilon;</sub>:x&gt;x<sub>&epsilon;</sub> f(x)&le;&epsilon;g(x)</code>
> <code>f(x)=o(g(x)) && f(x)=O(g(x))</code>
> *f(x) is in big and little o*
> ...
> now suppose
> <code>f(x)=x<sup>2</sup> g(x)=x<sup>2</sup> </code>
> *They are growing at the same rate, `f(x)` in NOT `o(g(x))`, but it is `O(g(x))`*
> If f(x) is o(g(x)) it will also be O(g(x)), but not the opposite.

### Other types of Asymptotic Relationships
- Big-Omega notation:
<code>f(x)=&Omega;(g(x)) iff g(x)=O(f(x))</code> *&Omega; is inverse of O*
> Interpretation: f(x) is bounded below by g(x)
- Big-Theta notation:
<code>f(x)=&Theta;(g(x)) iff f(x)=O(g(x)) and g(x)=O(f(x))</code>
> Interpretation: f(x) is bounded above and below by g(x)

#### 1.5.4
> Q: If f(x) is &Theta;(g(x)), does that mean that f(x) and g(x) are the same function?
> `f(x)=O(g(x))` and `g(x)=O(f(x))`
> A: *No*

> A: <code>f(x)=1/2x<sup>2</sup>-x</code>
> <code>g(x)=x<sup>2</sup></code>
> `############`
> <code>m<sub>1</sub>=1</code> guess m1=1
> <code>1/2x<sup>2</sup>-x &le; x<sup>2</sup></code>
> <code>1/2x-1 &le; x</code>
> <code>-1 &le; 1/2x</code>
> <code>-2 &le; x</code>
> <code>x<sub>0</sub> &gt; -2</code>
> `#############`
> try <code>m<sub>2</sub>=4</code>
> <code>x<sup>2</sup> &le; 4(1/2x<sup>2</sup>-x)</code>
> <code>x &le; 2x-4</code>
> <code>4 &le; x</code>
> `##############`
> **m1=1 and m2=4, with x&gt;4 for &Theta;(n)**


**prof's answer**
> <code>f(x)=x<sup>2</sup></code>
> <code>f(x)=2x</code>
> `f(x)=O(g(x))`
> <code>f(x)&le;M g(x)</code> for x &gt; x<sub>0</sub>
> need to find m & x0 such that this is true.
> set m=1 and x0=1
> to prove g(x)=O(f(x))
> m=3, x0=1 for x>1

### Summary
|notation|interpretation|
|:-:|:-:|
|`f(x)=O(g(x))`| f(x) is asymptotically bounded above by g(x)|
|`f(x)=o(g(x))`| g(x) grows much faster than f(x)|
| <code>f(x)=&Theta;(g(x))</code>| f(x) and g(x) grow at roughly the same rate|
| <code>f(x)=&Omega;(g(x))</code>| f(x) is bounded by below by g(x)|

### Big-O Notation in Practice
- **simplification rules**
  - Only pay attention to the dominant terms x<sup>3</sup> more important than x<sup>2</sup>.
  - Don't include constants in your big-O expression.

### Big-O Notation and Limits
> *Theorem*: Let `f(x)` and `g(x)` be real-valued functions


Let $L=\lim_{x\to\infty}\frac{f(x)}{g(x)}$
> 1. <code>L=0, f(x)=o(g(x)) and f(x)=O(g(x))</code>
> *g(x) is growing much faster than f(x)*
> 2. <code>L=&infin;, g(x)=o(f(x)) and f(x)=&Omega;(g(x))</code>
> *f(x) is growing much faster than g(x)*
> 3. <code>0&lt;L&lt;&infin;, f(x)=&Theta;(g(x)) and f(x)=O(g(x))</code>
> *f(x) is growing at the same rate as g(x)*

### L'Hopital's Rule
What if f(x) and g(x) both = 0 or &infin; in the limit?

*L'Hopital's Rule*
If $\lim_{x\to\infty}f(x) = \lim_{x\to\infty}g(x) = 0 || \infty$, then $\lim_{x\to\infty}\frac{f(x)}{g(x)}=\lim_{x\to\infty}\frac{f'(x)}{g'(x)}$
*as long as the latter limit exists*


#### Example
> Q. What is the asymptotics relationship between `f(x)=x^2` and `g(x)=2^x`?
> A.
*Using L'Hopital's Rule...*
$L=\lim_{x\to\infin}\frac{f(x)}{g(x)}$
$\lim_{x\to\infin}\frac{x^{2}}{2^{x}}=\frac{\infin}{\infin}$
$\lim_{x\to\infty}\frac{f'(x)}{g'(x)}=\frac{2x}{ln(2)2^{x}}=\frac{\infin}{\infin}$
$\lim_{x\to\infty}\frac{f''(x)}{g''(x)}=\frac{2}{ln^{2}(2)2^{x}}=\frac{2}{\infin}=0$
> <code>L=0, f(x)=o(g(x)) and f(x)=O(g(x))</code>
> <code>x<sup>2</sup>=o(2<sup>x</sup>)</code>
> `g(x)` is growing much faster than `f(x)` as we can see.

#### Example
> Q. Find a function `g(x)` such that <code>f(x)=5x<sup>4</sup>+3x<sup>2</sup>+10000</code> is `O(g(x))` with proof.
> A. 
> *claim*: $g(x)=x^{4}$ is a function such that $5x^{4}+3x^{2}+10000$=O(g(x))
> *proof*: Using the *limit theorem*...
> $\lim_{x\to\infin}\frac{f(x)}{g(x)}=\lim_{x\to\infin}\frac{f5x^{4}+3x^{2}+10000}{x^{4}}=\frac{\infin}{\infin}$
> *using L'Hoptial's rule...*
> $\lim_{x\to\infin}\frac{f^{4}(x)}{g^{4}(x)}=5$
> Since the limit is 0&lt;L&lt;&infin;, we have proven that g(x) is at the same rate as f(x) than f(x), thus f(x)=O(g(x)) and f(x)=&Theta;(g(x))


### Some running time functions that computer scientists like
- polynomial time: $O(n^{4}),O(n^{2})$
- logarithmic: $O(log(n))$
- quasilinear: $O(n*log(n)$ *fairly common*
- sublinear: $O(n^{\frac{1}{2}})$ *this is the best!*
- exponential: $O(2^{x})$ *Very bad! Often indicates something that is basically brute force...*