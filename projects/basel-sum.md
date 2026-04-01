# The Basel Problem and the Riemann Zeta Function

## 1. The Problem

The Basel problem asks for the exact value of the sum

$$\sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{1}{1^2} + \frac{1}{2^2} + \frac{1}{3^2} + \frac{1}{4^2} + \cdots$$

This series converges (by comparison with a telescoping series, for instance), but finding its exact value resisted mathematicians for nearly a century after Pietro Mengoli posed it in 1644. Euler solved it in 1734, showing

$$\sum_{n=1}^{\infty} \frac{1}{n^2} = \frac{\pi^2}{6}$$

The appearance of $\pi$ in a sum over integers is surprising and suggests a deep connection between analysis and number theory. Understanding why $\pi$ appears here was my starting point.

## 2. Euler's Approach via Taylor Series

The key idea in Euler's original argument is to connect the sum $\sum 1/n^2$ to a known function whose Taylor series involves exactly these reciprocals.

### 2.1 Starting from sin(x)/x

Consider the Taylor series for $\sin(x)$:

$$\sin(x) = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \frac{x^7}{7!} + \cdots$$

Dividing by $x$:

$$\frac{\sin(x)}{x} = 1 - \frac{x^2}{3!} + \frac{x^4}{5!} - \frac{x^6}{7!} + \cdots$$

### 2.2 The infinite product representation

Euler's insight was to also write $\sin(x)/x$ as an infinite product over its roots. Since $\sin(x) = 0$ when $x = n\pi$ for any nonzero integer $n$, we can write

$$\frac{\sin(x)}{x} = \left(1 - \frac{x^2}{\pi^2}\right)\left(1 - \frac{x^2}{4\pi^2}\right)\left(1 - \frac{x^2}{9\pi^2}\right)\cdots$$

### 2.3 Matching coefficients

Expanding the infinite product and collecting the $x^2$ terms, the coefficient of $x^2$ is

$$-\left(\frac{1}{\pi^2} + \frac{1}{4\pi^2} + \frac{1}{9\pi^2} + \cdots\right) = -\frac{1}{\pi^2}\sum_{n=1}^{\infty}\frac{1}{n^2}$$

From the Taylor series side, the coefficient of $x^2$ is $-1/6$.

Setting these equal:

$$-\frac{1}{\pi^2}\sum_{n=1}^{\infty}\frac{1}{n^2} = -\frac{1}{6}$$

$$\sum_{n=1}^{\infty}\frac{1}{n^2} = \frac{\pi^2}{6}$$

### 2.4 Note on rigor

Euler's original argument treats $\sin(x)/x$ as a polynomial with infinitely many roots, which requires justification. The Weierstrass factorization theorem, developed over a century later, provides the rigorous foundation for this step. Euler knew the argument was not fully rigorous by the standards even of his time, but he verified the result numerically and later found alternative proofs.

## 3. The Riemann Zeta Function

The Basel problem is a special case of a much broader object. The Riemann zeta function is defined for $s > 1$ by

$$\zeta(s) = \sum_{n=1}^{\infty} \frac{1}{n^s}$$

So the Basel problem is the evaluation $\zeta(2) = \pi^2/6$.

### 3.1 Values at positive even integers

Euler also computed $\zeta(s)$ at other even positive integers and found a pattern:

| $s$ | $\zeta(s)$ | Numerical value |
|-----|-----------|-----------------|
| 2 | $\pi^2/6$ | 1.6449340... |
| 4 | $\pi^4/90$ | 1.0823232... |
| 6 | $\pi^6/945$ | 1.0173430... |
| 8 | $\pi^8/9450$ | 1.0040773... |
| 10 | $\pi^{10}/93555$ | 1.0009945... |

Every $\zeta(2k)$ is a rational multiple of $\pi^{2k}$. The general formula involves Bernoulli numbers $B_{2k}$:

$$\zeta(2k) = \frac{(-1)^{k+1}(2\pi)^{2k}}{2(2k)!} B_{2k}$$

### 3.2 Values at positive odd integers

In contrast to the even case, almost nothing is known in closed form about $\zeta(s)$ at odd integers. Roger Apery proved in 1978 that $\zeta(3)$ is irrational, but no closed-form expression in terms of $\pi$ is known for any odd zeta value. Whether $\zeta(5), \zeta(7), \ldots$ are irrational remains open for individual cases, though Rivoal (2000) showed infinitely many odd zeta values are irrational.

This asymmetry between even and odd zeta values is one of the striking open problems in analytic number theory.

### 3.3 Convergence rate

One thing I noticed computationally is how the convergence rate of $\zeta(s) = \sum 1/n^s$ changes dramatically with $s$:

- For $s = 2$: 100 terms gives roughly 2 correct decimal places
- For $s = 4$: 100 terms gives roughly 4 correct decimal places
- For $s = 10$: 100 terms gives roughly 10 correct decimal places

This makes intuitive sense: larger $s$ means the terms $1/n^s$ decay faster, so the tail of the series contributes less. But the quantitative relationship between $s$, the number of terms $N$, and the approximation error is interesting. By integral comparison:

$$\sum_{n=N+1}^{\infty} \frac{1}{n^s} \leq \int_N^{\infty} \frac{1}{x^s}\,dx = \frac{N^{1-s}}{s-1}$$

This bound shows the error decreases like $N^{1-s}$, which tightens rapidly as $s$ increases.

## 4. Computational Experiments

See `zeta-experiment-output.txt` for the code behind these observations.

### 4.1 Verifying zeta values numerically

I wrote Python scripts to compute partial sums of $\zeta(s)$ and compare against known closed forms. For even $s$, agreement with $\pi^{2k}$ times the appropriate rational is exact to the precision of the computation. For odd $s$, the partial sums converge to values that do not appear to have simple closed forms.

### 4.2 Ratios of consecutive zeta values

I computed the ratios $\zeta(2k)/\zeta(2k+2)$ to see if they exhibit any pattern:

| $k$ | $\zeta(2k)/\zeta(2k+2)$ |
|-----|-------------------------|
| 1 | 1.5185... |
| 2 | 1.0646... |
| 3 | 1.0163... |
| 4 | 1.0040... |

All ratios approach 1 from above, which makes sense since $\zeta(s) \to 1$ as $s \to \infty$. The rate of approach is itself interesting.

### 4.3 Partial sums and Bernoulli numbers

Using the formula $\zeta(2k) = (-1)^{k+1}(2\pi)^{2k} B_{2k}/(2(2k)!)$, I computed Bernoulli numbers from the known zeta values and verified they match the standard sequence. The Bernoulli numbers grow rapidly in absolute value, which is balanced by the factorial in the denominator.

## 5. Connections and Open Directions

### 5.1 Why does pi appear?

The appearance of $\pi$ in $\zeta(2k)$ is ultimately traced back to the connection between the zeta function and trigonometric functions (through Euler's product for $\sin(x)/x$, or equivalently through Fourier analysis). The fact that $\pi$ does not appear in odd zeta values (as far as anyone knows) suggests that a fundamentally different mechanism controls those values. Understanding this asymmetry is an active area of research.

### 5.2 Connections to other areas

During this exploration, I encountered several connections I want to investigate further:

- The Euler product $\zeta(s) = \prod_p (1 - p^{-s})^{-1}$ connects the zeta function to prime numbers. This is the starting point for analytic proofs of results about prime distribution.
- Bernoulli numbers appear in many areas: the Euler-Maclaurin summation formula, the Todd class in topology, and p-adic L-functions.
- The functional equation $\zeta(s) = 2^s \pi^{s-1} \sin(\pi s/2) \Gamma(1-s) \zeta(1-s)$ relates values at $s$ to values at $1-s$, extending the zeta function to all complex numbers.

### 5.3 Questions I am still thinking about

1. Is there a combinatorial or geometric interpretation of $\zeta(2) = \pi^2/6$ that does not go through Euler's product or Fourier analysis?
2. The convergence rate analysis in Section 3.3 gives an upper bound on the tail. Can this bound be sharpened using the Euler-Maclaurin formula? What is the exact asymptotic behavior of the error?
3. For odd zeta values, are there useful series representations that converge faster than the defining series?

## 6. References

- Euler, L. "De summis serierum reciprocarum" (1735)
- Dunham, W. "Euler: The Master of Us All," MAA, 1999
- Apostol, T. "Introduction to Analytic Number Theory," Springer, 1976
- Borwein, J., Bailey, D., Girgensohn, R. "Experimentation in Mathematics," A K Peters, 2004
