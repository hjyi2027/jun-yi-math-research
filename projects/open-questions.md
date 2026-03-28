# Open Questions and Future Directions

These are questions and patterns I encountered during my explorations that I have not resolved. Some are well-known open problems; others are specific to computations I ran.

## 1. The even/odd asymmetry

**Observation:** Every $\zeta(2k)$ has a closed form as a rational multiple of $\pi^{2k}$, but no $\zeta(2k+1)$ has a known closed form.

**Question:** Is there a structural reason for this asymmetry that can be understood without the full machinery of the functional equation? Euler's proof for $\zeta(2)$ uses the product formula for $\sin(x)/x$, whose roots are at integer multiples of $\pi$. Is there an analogous function whose root structure would give information about odd zeta values?

**What I've tried:** I looked at the product formula for $\cos(x)$, which has roots at odd multiples of $\pi/2$. Expanding and matching coefficients gives identities involving sums of the form $\sum 1/(2n-1)^{2k}$, but these reduce to known even zeta values via the relation $\sum 1/(2n-1)^s = (1 - 2^{-s})\zeta(s)$. So this approach circles back to even values.

## 2. Convergence acceleration

**Observation:** The Euler-Maclaurin correction dramatically improves partial sum accuracy for $\zeta(s)$. With just $N = 100$ terms plus a two-term correction, I get 4+ correct digits for $\zeta(2)$, compared to roughly 2 digits from the raw partial sum.

**Question:** How far can this be pushed? If I include more Bernoulli correction terms in the Euler-Maclaurin formula, how does the error scale? Is there an optimal number of correction terms for a given $N$, beyond which the asymptotic series starts diverging?

**What I know:** The Euler-Maclaurin series is asymptotic, not convergent, so including too many correction terms eventually makes the approximation worse. I want to understand this tradeoff computationally.

## 3. Rate of approach of $\zeta(s) \to 1$

**Observation:** As $s \to \infty$, $\zeta(s) \to 1$ because all terms $1/n^s$ for $n \geq 2$ vanish. Computationally:

| $s$ | $\zeta(s) - 1$ |
|-----|----------------|
| 2 | 0.6449... |
| 5 | 0.0369... |
| 10 | 0.000995... |
| 20 | 0.00000095... |

**Question:** The dominant term in $\zeta(s) - 1$ is $1/2^s$, the first non-trivial term of the series. How well does $\zeta(s) - 1 \approx 1/2^s$ hold? What is the next correction? From the series, $\zeta(s) - 1 - 1/2^s = 1/3^s + 1/4^s + \cdots$, so the next term is $1/3^s$. Is $\zeta(s) - 1 - 1/2^s - 1/3^s \sim 1/4^s$ a useful approximation, or does the error behavior change?

## 4. Bernoulli number growth

**Observation:** The Bernoulli numbers $|B_{2k}|$ grow extremely fast. From the formula $\zeta(2k) = |B_{2k}| \cdot (2\pi)^{2k} / (2(2k)!)$, and since $\zeta(2k) \to 1$, we get the asymptotic $|B_{2k}| \sim 2(2k)! / (2\pi)^{2k}$.

**Question:** This means Bernoulli numbers grow roughly like $(2k/(\pi e))^{2k}$ by Stirling. Is there a direct combinatorial or algebraic explanation for this growth rate that does not go through the zeta function?

## 5. Connections to the Euler product

The Euler product $\zeta(s) = \prod_p (1 - p^{-s})^{-1}$ encodes the fundamental theorem of arithmetic in analytic form. Taking logarithms:

$$\log \zeta(s) = -\sum_p \log(1 - p^{-s}) = \sum_p \sum_{k=1}^{\infty} \frac{p^{-ks}}{k}$$

**Question:** For $s = 2$, this gives $\log(\pi^2/6)$ as a sum over primes. Is this sum useful for extracting information about primes, or is it too "smooth" to detect individual prime behavior?

## 6. Generalizations I want to explore

- **Dirichlet L-functions:** Replace $\sum 1/n^s$ with $\sum \chi(n)/n^s$ for a Dirichlet character $\chi$. How do the special values of L-functions compare to zeta values?
- **p-adic zeta functions:** Kubota-Leopoldt p-adic L-function interpolates even zeta values p-adically. Can I understand this computationally?
- **Multiple zeta values:** Sums of the form $\sum_{n_1 > n_2 > \cdots > n_k \geq 1} \frac{1}{n_1^{s_1} \cdots n_k^{s_k}}$. What algebraic relations exist among these?
