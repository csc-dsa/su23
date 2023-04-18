<style>
  .red {color:red}
  .blue {color:#7cc7f9}
  .dblue {color:#011636}
  .green {color:green}
  .orange {color:orangered}
  .purple {color:purple}
  .brown {color:brown}
  iframe {width: 100%; height: 800px}
  .fa-rocket {display: none;}
</style>

# Recurrences

`````````` {div} full-width
````` {dropdown} <iframe width="100%" height="600" src="https://www.youtube.com/embed/B0NtAFf4bvU" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

``` {card} TL;DR
Recurrence relations are mathematical expressions that define the runtime of algorithms or the space complexity of data structures recursively in terms of their input size. In other words, they describe the time or space complexity of an algorithm by expressing it as a function of the size of the input data.

In the context of data structures and algorithms, recurrences are commonly used to analyze the performance of recursive algorithms such as quicksort, mergesort, and binary search. By using recurrence relations, we can obtain a closed-form expression for the runtime complexity of such algorithms and make predictions about their performance as the input size grows.

Solving recurrence relations can be challenging, and there are several methods to do so, including the substitution method, the recursion tree method, and the master theorem. Understanding and using recurrence relations is an important skill for anyone studying data structures and algorithms, as it enables them to analyze the performance of algorithms and design more efficient solutions.
```

``` {card} Additional Resources

```
`````
<!-- ``` {image} https://cdn-images-1.medium.com/max/1200/1*3Kti9X9KAL0_XCk1cdjbDw.jpeg
:align: center
``` -->
``````````

<!-- ## MTH 180 Review

### Sequences

`````````` {div} full-width
`````````  {admonition} Definition 1
> A *sequence* is a function from a subset of the set of integers (usually either the set $\{0, 1, 2,… \}$
or the set $\{1, 2, 3,… \}$) to a set $S$. We use the notation $a_n$ to denote the image of the integer $n$.
We call $a_n$ a term of the sequence.
> 
> -- *Discrete Mathematics and Its Applications*

```` {card} Example

Consider the sequence $\{a_n\}$, where

$$a_n = \frac{1}{n}$$

The list of the terms of this sequence, beginning with $a_1$, namely, $\{a_1, a_2, a_3, a_4,… \}$
starts with

$$ 1, \frac{1}{2}, \frac{1}{3}, \frac{1}{4}, \dots $$
`````````
````````` {admonition} Definition 2
> A *geometric progression* is a sequence of the form
> $a, ar, ar^2, \dots, ar^n, \dots $
where the initial term $a$ and the common ratio $r$ are real numbers.
> 
> -- *Discrete Mathematics and Its Applications*

```` {card} Example
The sequences

$\{b_n\}$ with $b_n = (−1)^n$,  
$\{c_n\}$ with $c^n = 2 ⋅ 5^n$,  
$\{d_n\}$ with $d_n = 6 ⋅ (\frac{1}{3})^n$   

...are geometric progressions with initial term and common ratio equal to 

$1$ and $−1$,  
$2$ and $5$,  
$6$ and $\frac{1}{3}$

If we start at $n = 0$ for the following lists of terms...what will each begin with?

``` {dropdown} $b_0, b_1, b_2, b_3, b_4, \dots $

$$1, −1, 1, −1, 1, \dots$$
```
``` {dropdown} $c_0, c_1, c_2, c_3, c_4, \dots $

$$ 2, 10, 50, 250, 1250, \dots$$
```
``` {dropdown} $d_0, d_1, d_2, d_3, d_4, \dots$

$$6, 2, \frac{2}{3}, \frac{2}{9}, \frac{2}{27}, \dots $$ 
```
````

`````````
````````` {admonition} Definition 
> An *arithmetic progression* is a sequence of the form 
> $a, a + d, a + 2d, \dots , a + nd, \dots$ 
> where the initial term $a$ and the common difference $d$ are real numbers.
> 
> -- *Discrete Mathematics and Its Applications*

```` {card} Example
The sequences 

$\{s_n\}$ with $s_n = −1 + 4n$  
$\{t_n\}$ with $t_n = 7 − 3n$

...are both arithmetic progressions with initial terms and common differences equal to 

$−1$ and $4$  
$7$ and $−3$

If we start at $n = 0$ for the following lists of terms...what will each begin with?

``` {dropdown} $s_0, s_1, s_2, s_3, \dots $

$$−1, 3, 7, 11, \dots $$
```
``` {dropdown} $t_0, t_1, t_2, t_3, \dots $

$$7, 4, 1, −2, \dots $$
```
````

`````````
``````````

### Summation Notation

`````````` {div} full-width
````````` {admonition} Definition 
> If $m$ and $n$ are integers and $m \le n$, the symbol $\Sigma_{k = m}^{n} a_k$  
> read the **summation from $k$ equals $m$ to $n$ of $a_k$**, 
> is the sum of all the terms $a_m, a_{m+1}, a_{m+2}, \dots , a_n$.
> We say that $a_m, a_{m+1}, a_{m+2}, \dots , a_n$ is the expanded form of the sum, and
we write
> 
> $$\Sigma_{k=m}^{n} a_k = a_m + a_{m+1}, a_{m+2}, \dots , a_n$$
> 
> We call $k$ the **index** of the summation, $m$ the **lower limit** of the summation, and $n$
the **upper limit** of the summation.
> 
> -- *Discrete Mathematics with Applications, 4th*

```` {card} Examples
Let $a_1 = −2,\ a_2 = −1,\ a_3 = 0,\ a_4 = 1,\ and\ a_5 = 2$. Compute the following:

``` {dropdown} $\Sigma_{k=1}^{5} a_k$
$$\begin{align}
\Sigma_{k=1}^{5} a_k & = a_1 + a_2 + a_3 + a_4 + a_5 \\
& = (−2) + (−1) + 0 + 1 + 2 \\
& = 0
\end{align}$$
```

``` {dropdown} $\Sigma_{k=2}^{2} a_k$
$$\begin{align}
\Sigma_{k=2}^{2} a_k & = a_2 \\
& = −1 \\
\end{align}$$
```

``` {dropdown} $\Sigma_{k=1}^{2} a_{2k}$
$$\begin{align}
\Sigma_{k=1}^{2} a_{2k} & = a_{2*1} + a_{2*2} \\
& = a_2 + a_4 \\
& = -1 + 1 \\
& = 0
\end{align}$$
```



````

`````````

`````````` -->



## Factorial of n (formula)

`````````` {div} full-width
`````` {card} $n!$

> For each positive integer $n$, the quantity **$n$ factorial** denoted $n!$, is defined to be the
product of all the integers from $1$ to $n$:  
>
> $$n! = n · (n − 1) \dots 3·2·1$$  
>
> **Zero factorial**, denoted 0!, is defined to be 1:  
>
> $$0! = 1$$ 
> 
> -- *Discrete Mathematics with Applications, 4th*
``````
`````` {card} Examples
Simplify the following expressions:

````` {grid}
```` {grid-item}
:columns: 3
``` {dropdown} $\frac{8!}{7!}$
$$\begin{align}
\frac{8!}{7!} & = \frac{8 * 7!}{7!} \\
& = 8 \\
\end{align}$$
```
````
```` {grid-item}
:columns: 4
``` {dropdown} $\frac{5!}{2!*3!}$
$$\begin{align}
\frac{5!}{2!*3!} & = \frac{5 * 4 * 3!}{2! *3!} \\
& = \frac{5 * 4}{2 * 1} \\
& = \frac{20}{2} \\
& = 10 \\
\end{align}$$
```
````
```` {grid-item}
:columns: 5
``` {dropdown} $\frac{(n)!}{(n - 3)!}$
$$\begin{align}
\frac{(n)!}{(n - 3)!} & = \frac{n * (n - 1) * (n - 2) * (n - 3)!}{(n - 3)!} \\
& = n * (n - 1) * (n - 2) \\
& = n^3 - 3n^2 + 2n
\end{align}$$
```
````
`````
``````


```` {admonition} code
```{code-block} cpp
:lineno-start: 1
:emphasize-lines:
int fact(int num) {

  if (num == 0) return 1;

  else return num * fact(num - 1);   
}
```
[https://www.geeksforgeeks.org/factorial-formula/](https://www.geeksforgeeks.org/factorial-formula/)  
````

```````` {card} Use Cases
```````  {grid}
``````   {grid-item}
:columns: 6
````` {admonition} Permutation
- gives the number of ways to select $r$ elements from $n$ elements when *_order matters_*

$$^nP_r = \frac{n!}{(n – r)!}$$

```` {card} Example
Three different fruits are to be distributed among a group of 10 people. Find the total number of ways this can be possible.

``` {dropdown} $n = 10,\ r = 3 \dots =\ ^{10}P_3$
$$\begin {align}
n = 10,\ r = 3...\ &=\ ^{10}P_3 \\
&= \frac{10!}{(10 – 3)!} \\
&= \frac{10!}{7!} \\ 
&= \frac{10 × 9 × 8 × 7!}{7!} \\
&= 10 × 9 × 8 \\
&= 720
\end {align}$$
```
````
`````
``````
`````` {grid-item}
:columns: 6
````` {admonition} Combination
- gives the number of ways to select $r$ elements from $n$ elements where *_order does not matter_*

$$^nC_r = \frac{n!}{r! (n – r)!}$$

```` {card} Example
Find the number of ways 3 students can be selected from a class of 50 students.
``` {dropdown} $n = 50,\ r = 3 \dots =\ ^{50}C_3$
$$\begin {align} 
n = 50,\ r = 3...\ &=\ ^{50}C_3 \\
&= \frac{50!}{3! × 47!} \\
&= \frac{50 × 49 × 48 × 47!}{3! × 47!} \\
&= \frac{50 ×49 × 48}{6} \\
&= 19,600
\end {align}$$
```
````
`````
``````
```````

``````````

## Analysis of Binary Search

`````````` {div} full-width
``````` {card}
```{code-block} cpp
:lineno-start: 1
:emphasize-lines:
int bsearch(int *A, int lo, int hi, int k) {
  
    //base case
    if (hi < lo) return NOT_FOUND;
    
    // calculate mid point index
    int mid = lo + ( (hi - lo) / 2);
    
    // key found?
    if (A[mid] == k) return mid;
    
    // key in upper subarray?
    if (A[mid] < k) return bsearch(A, mid + 1, hi, k);
    
    // key is in lower subarray?
    return bsearch(A, lo, mid - 1, k);
}
```
``` {card} cases
$$T(n) = {1\space\space\space\space\space\space\space\space\space\space\space\space\space\space\space\space\space\space\space\space\space\space if\ n = 1 \brace T(\frac{n}{2}) + n\space\space\space\space\space\space\space if\ n > 1}$$
```
```````
``````````

## [Recurrence relations](https://www.math.wichita.edu/discrete-book/ch_sequences.html)

`````````` {div} full-width
```` {card}
By itself, a recurrence does not describe the running time of an algorithm
- need a *closed-form* solution (non-recursive description)
- exact closed-form solution may not exist, or may be too difficult to find

For most recurrences, an asymptotic solution of the form $\Theta()$ is acceptable
- ...in the context of analysis of algorithms
````
``````````

### [How to solve recurrences?](https://courses.engr.illinois.edu/cs473/sp2010/notes/99-recurrences.pdf)

`````````` {div} full-width
```` {card} Solving recurrances

``` {card} [Unrolling](https://courses.cs.washington.edu/courses/cse332/18su/handouts/unrolling.pdf)
Expanding the recurrence
: a.k.a. *iteration method* or repeated substitution

Keep unrolling the recurrence until you identify a general case
: then use the base case

Not trivial in all cases but it is helpful to build an intuition
: may need induction to prove correctness
```

``` {card} [Guessing](https://www.geeksforgeeks.org/method-of-guessing-and-confirming/)
- the answer and proving it correct *by induction*
```

``` {card} Recursion Tree
```

``` {card} [Master Theorem](http://homepages.math.uic.edu/~leon/cs-mcs401-s08/handouts/master_theorem.pdf)
```

````
``````````

### [Unrolling the binary search recurrence](https://youtu.be/XcZw01FuH18)

`````````` {div} full-width
```````` {card}

``````` {admonition} [Binary Search Recursive Method](https://youtu.be/uEUXGcc2VXM)

``` {code-block} cpp
:lineno-start: 1
:emphasize-lines: 1-2,7-10

void RBinSearch(l, h, key) {                                // = T(n)
  if (l == h) {                                             // = 1
    if (A[l] == key) return l;
    else return 0;
  }
  else {                                    
    mid = (l + h)/2;                                        // = 1
    if (key == A[mid]) return mid;                          // = 1
    if (key < A[mid]) return RBinSearch(l, mid - 1, key);   // = 1
    else return RBinSearch(mid + 1, h, key);                // = T(n/2)
  }
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$n = 1$}  \\[2ex]
T(\frac{n}{2}) + 1, & \text{$n \gt 1$}
\end{cases}
$$

```````

````````
``````````

## Recurrence Relations

`````````` {div} full-width
````````` {card}

```````` {admonition} [Recurrence Relation: Dividing Function](https://youtu.be/8gt0D0IqU5w)

```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 1, 3, 4
void Test(int n) {       // = T(n)
  if (n > 0) {
    printf("/d", n);     // = 1
    Test(n/2);           // = T(n/2) 
  }
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$n = 1$}  \\[2ex]
T(\frac{n}{2}) + 1, & \text{$n \gt 1$}
\end{cases}
$$

``````` {card} Tree Method
`````` {grid}
````` {grid-item-card}
``` {image} imgs/10_rec_bin_search_tree.png
```
`````
````` {grid-item-card}
$$\begin {align}
For \dots \frac{n}{2^k} & = 1 \\
Assume \dots n & = 2^k \\
Then \dots k & = log\ n \\
& = \Theta(log\ n) \\
\end {align} $$
`````
``````
```````

``````` {card} Substitution Method
`````` {grid}
`````  {grid-item-card}
:columns: 6

$$\begin {align}
T(n) & = T(\frac{n}{2}) + 1 \\
& = [T(\frac{n}{n^2}) + 1] + 1 \\
& = T(\frac{n}{n^2}) + 2 \\
& = T(\frac{n}{n^3}) + 3 \\
& • \\
& • \\
& • \\
& = T(\frac{n}{n^k}) + k \\
\end {align} $$
`````
````` {grid-item-card}
:columns: 6
What to sub in...

$$\begin {align}
T(n) & = T(\frac{n}{2}) + 1 \\
T(\frac{n}{2}) & = T(\frac{n}{2^2}) + 1 \\
\end {align} $$
`````
````` {grid-item-card}
$$\begin {align}
For \dots \frac{n}{2^k} & = 1 \\
Assume \dots n & = 2^k \\
Then \dots k & = log\ n \\
\\
T(n) & = T(1) + log\ n \\
& = 1 + log\ n \\
& = \Theta(log\ n) \\
\end {align} $$
`````
```````
````````


``````` {admonition} [Recurrence Relation: Linear](https://youtu.be/4V30R3I1vLI)

```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 1, 3, 4
void Test(int n) {       // = T(n)
  if (n > 0) {
    printf("/d", n);     // = 1
    Test(n - 1);         // = T(n - 1) 
  }
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$n\ = 0$}  \\[2ex]
T(n - 1) + 1, & \text{$n\ \gt 0$}
\end{cases}
$$

```` {admonition} Can you write (and solve) the recurrence?
:class: dropdown, tip

``` {card} Breakdown
$$\begin {align}
T(n) &= T(n - 1) + 1 \\
T(n - 1) &= T(n - 2) + 1 \\
T(n - 2) &= T(n - 3) + 1 \\ 
• \\
• \\
• \\
T(n - k) &= T(n - k) + 1 \\
\end {align}$$
```

``` {card} Substitution $T(n - 1)$
$$\begin {align}
T(n) &= \bigg[T(n - 2) + 1 \bigg] + 1 \\ 
&= T(n - 2) + 2 \\
&= \bigg[T(n - 3) + 1 \bigg] + 2 \\
&= T(n - 3) + 3 \\
• \\
• \\
• \\
&= T(n - k) + k \\
\end {align}$$ 
```

``` {card} For $k$ times

$$\begin {align}
\text{For : } & T(n) = T(n - k) + k \\
\text{Assume : } & n\ - k\ = 0 \\
\text{Therefore : } & n\ = k \\
\end {align}$$ 

$$\begin {align}
T(n) &= T(n - n) + n \\
T(n) &= T(0) + n \\
• \\
T(n) &= 1 + n \\
T(n) &= \Theta(n) \\
&= \Theta(n) \\
\end {align}$$

```

````
```````

``````` {admonition} [Recurrence Relation: Divide & Conquer](https://youtu.be/1K9ebQJosvo)

```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 1, 3, 6, 7
void Test(int n) {              // = T(n)
  if (n > 1) {
    for(i = 0; i < n; i++>) {   // = n
      // some statement
    }
    Test(n/2);                  // = T(n/2)
    Test(n/2);                  // = T(n/2)
  }
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$if\ n\ = 1$}  \\[2ex]
2T(\frac{n}{2}) + n, & \text{$if\ n\ \gt 1$}
\end{cases}
$$

````` {admonition} Can you write (and solve) the recurrence?
:class: dropdown, tip

```` {card} Tree Method
``` {figure} imgs/10_ex_2.png
:width: 100%
```

$$
For\ k\ times\ = \frac{n}{2^k}\ \Rightarrow\ n = 2^k \\
Hence,\ k\ = log\ n \\
T(n) = \Theta(n\ log\ n)
$$
````

````` {card} Substitution Method

```` {grid}
``` {grid-item}
$$\begin {align}
T(n) &= 2T(\frac{n}{2}) + n \\
&= 2\bigg[2T(\frac{n}{2^2}) + \frac{n}{2}\bigg] + n \\
&= 2^2T(\frac{n}{2^2} + n + n) \\
&= 2^2\bigg[2T(\frac{n}{2^3}) + \frac{n}{2^2}\bigg] + 2n \\
&= 2^3T(\frac{n}{2^3}) + 3n \\
&= 2^kT(\frac{n}{2^k}) + kn \\
\end {align}$$
```
``` {grid-item}
*What to sub in...*

$$\begin {align}
T(n) &= 2T(\frac{n}{2}) + n \\
T(\frac{n}{2}) &= 2T(\frac{n}{n^2}) + \frac{n}{2^2} \\
T(\frac{n}{2^2}) &= 2T(\frac{n}{2^3}) + \frac{n}{2^2} \\
\end {align}$$
```
``` {grid-item}
$$
Assume...\ T(\frac{n}{2^k}) = T(1) \\
\frac{n}{2^k} = 1 \\
$$
```
``` {grid-item}
$$
Therefore...\ n\ = 2^k \\
k\ = log\ n \\
$$
```
``` {grid-item}
$$\begin {align}
T(n) &= 2^kT(1) + kn \\
&= n * 1 + n\ log\space n \\
&= \Theta(n\space log\space n) \\
\end {align}$$
```

````

`````
```````

``````` {admonition} [Recurrence Relation: Tower of Hanoi](https://youtu.be/1K9ebQJosvo) 

```{code-block} cpp
:lineno-start: 1
:emphasize-lines: 1 - 4
void Test(int n) {    // = T(n)
  printf("/d", n);    // = 1
  Test(n - 1);        // = T(n - 1)
  Test(n - 1);        // = T(n - 1)
}
```

$$
T(n) =
\begin{cases}
1,  & \text{$if\ n\ = 0$}  \\[2ex]
2T(n - 1) + 1, & \text{$if\ n\ \gt 0$}
\end{cases}
$$

`````` {admonition} Can you write (and solve) the recurrence?
:class: dropdown, tip

````` {card} Tree Method
```` {figure} imgs/10_ex_3.png
````

```` {card} Breakdown
$$\begin {align}
1 + 2 + 2^2 + 2^3 ... + 2^k & = 2^{k + 1} - 1 \\
\\
ar + ar + ar^2 + ar^3 ... + ar^k & = \frac{a(r^{k + 1} - 1)}{r - 1} \\
\\
Where \dots a = 1,  r = 2,  & = \frac{1(2^{k + 1}1)}{2 - 1} \\
\\
& = 2^{k + 1} - 1
\end {align} $$
````

```` {card} Assume
$$\begin {align}
if \dots n - k & = 0 \\
\\
then \dots n & = k \\
& = 2^{k + 1} - 1 => 2^{n + 1} - 1 \\
& = \Theta(2^n) \\
\end {align}$$
````

`````

````` {card} Substitution
```` {grid} 
``` {grid-item}
$$\begin {align}
T(n) &= 2T(n - 1) + 1 \\
& = 2\bigg[2T(n - 2) + 1 \bigg] + 1 \\
& = 2^2T(n - 2) + 2 + 1 \\
& = 2^2 \bigg[2T(n - 3) + 1 \bigg] + 2 + 1 \\
& = 2^3T(n - 3) + 2^2 + 2 + 1 \\
& • \\
& • \\
& • \\
& = 2^kT(n - k) + 2^k-1 + 2^k-2 + ... 2^2 + 2 + 1 \\
\end {align}$$
```
``` {grid-item}
$$\begin {align}
Assume \dots n - k = 0 \\
\\
n = k \\
\\
T(n) & = 2^nT(0) + 1 + 2 + 2^2\ + \dots\ 2^k-1 \\
& = 2^n - 1 + 2^k - 1 \\
& = 2^n + 2^n - 1 \\
& = 2^n+1 - 1 \\
& = \Theta(2^n) \\
\end {align}$$
```
````
`````
``````
```````

``````` {admonition} [Master Theorem](https://youtu.be/2H0GKdrIowU)

`````` {tab-set}
`````  {tab-item} Cases
If $T(n) = aT(\frac{n}{b}) + O(n^d)$ (for constants $a \gt 0, b \gt 1, d \ge 0$), then:

$$
T(n) =
\begin{cases}
O(n^d),  & \text{$if\ d\ \gt log_b\ a$}, && Case 1 \\[2ex]
O(n^d\ log\ n),  & \text{$if\ d\ = log_b\ a$}, && Case 2 \\[2ex]
O(n^{log_b\ a}),  & \text{$if\ d\ \lt log_b\ a$}, && Case 3 \\
\end{cases}
$$
`````
`````  {tab-item} Case 1

$$T(n) = 2T(\frac{n}{2}) + O(n^2)$$

$$\begin {align}
a & = 2 \\
b & = 2 \\
c & = 2 \\
\\
\end{align}$$

Since $d \gt log_b\ a$, $T(n) = O(n^d) = O(n^2)$
`````
`````  {tab-item} Case 2

$$T(n) = T(\frac{n}{2}) + O(1)$$

$$\begin {align}
a & = 1 \\
b & = 2 \\
c & = 0 \\
\\
\end{align}$$

Since $d = log_b\ a$,

$$\begin {align}
T(n) & = O(n^d\ log\ n) \\
& = O(n^0\ log\ n) \\
& = O(log\ n) \\
\end{align}$$
`````
`````  {tab-item} Case 3

$$T(n) = 4T(\frac{n}{2}) + O(n)$$

$$\begin {align}
a & = 4 \\
b & = 2 \\
c & = 1 \\
\\
\end{align}$$

Since $d \lt log_b\ a$, $T(n) = O(n^{log_b\ a}) = O(n^2)$
`````
``````
``````````
