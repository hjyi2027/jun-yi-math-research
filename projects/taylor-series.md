# Taylor Series and Convergence

This project explores how Taylor series can be used to approximate functions, how convergence works, and where Taylor approximation succeed or fail.

## 1. Introduction
Taylor series are approximations around a local point that turn non-polynomial functions into polynomial functions using all orders of the function's derivatives at that point.


## 2. Definitions and Basics
The Taylor series of a function $f(x)$ centered at $a$ is given by:

[Taylor Series Formula] 

$$f(x) = \sum_{n=0}^\infty \frac{f^{(n)}(a)}{n!} {(x-a)}^n$$

SPECIAL CASE:
When $a$ = 0,
We use the Maclaurin series; series identical to Taylor series with $a$ evaluated as 0.


Radius of convergence is the range where the series equals the function’s values. Outside the radius of convergence, the series diverges from the function’s behavior.

Mclaurin series for:

1. $f(x)$ = $e^x$

$e^x$ = 1 + $x$ + $\frac{x^2}{2!}$ + $\frac{x^3}{3!}$ + $\frac{x^4}{4!}$ .... + $\frac{x^n}{n!}$ (the series converges for all real numbers since the series as a whole converges for every $x$)

2. $f(x)$ = $sin(x)$

$sin(x)$ = 0 + $x$ - $x^3$ + $x^5$ - $x^7$ ..... + $(-1)^{n-1}(x^{n-1})$ + $(-1)^n x^n$ (The series converges for all $x$ based on applying the ratio test, which shows the radius of convergence is infinite)

3. $f(x)$ = $ln(x+1)$

$ln(x+1)$ = 0 + $x$ - $\frac{x^2}{2}$ + $\frac{x^3}{3}$ - $\frac{x^4}{4}$ ...... + $(-1)^{n-1} (\frac{x^{n-1}}{n-1})$ + $(-1)^n \frac{x^n}{n}$(convergence range: (-1,1])


## 3. Visualization and Error
- How the approximation improves with higher-degree polynomials
- Graphs comparing function vs. Taylor approximation
- Error term (briefly)

## 4. Deeper Questions
- Why does the Taylor series of ln(x) fail at x=0?
- What happens outside the radius of convergence?

## 5. Python/Desmos Simulation (Optional)
- Plot f(x) and its Taylor approximations for eˣ or sin(x)

## 6. Reflection
- What did I learn?
- Why is this interesting?

## 7. References
- Link to notes, videos, or books you used
