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

In the previous sections, I defined Taylor and Maclaurin series and wrote down some concrete examples. In this section, I focus on how Taylor polynomials actually behave when graphed, how the approximation improves as the degree increases, and how the idea of an “error term” helps measure how good the approximation is.

### 3.1 How the approximation improves with higher degree

To see what a Taylor polynomial is really doing, it is useful to fix one function and compare several of its Taylor polynomials of different degrees.

For this section, I use all three functions from section 2 as a running example. As I increase the degree, two things happen:

(images/taylor series of e^x.gif)
(images/taylor series of sin(x).gif)
(images/taylor series of ln(x).gif)

1. The polynomial becomes a better match near the center.
2. The interval around the center where the polynomial stays close to the original function becomes wider.

If I look at the degree 1 polynomial (a tangent line approximation), it matches the function only very close to the center; moving even a little away, the line drifts off quickly. A degree 2 or degree 3 polynomial already follows the curvature of the function much better and stays close over a noticeably larger interval. For degree 5 or higher, the graph of the polynomial and the graph of the function often overlap so well near the center that it is hard to distinguish them by eye.

However, even high degree polynomials are not perfect. Far enough away from the center, the polynomial usually starts to misbehave: it may grow too fast, oscillate differently, or simply fail to follow the function’s shape. This illustrates a key idea: Taylor polynomials are local approximations. They are designed to be accurate near the center point, not necessarily everywhere.

### 3.2 Static and animated graphs of function vs Taylor polynomials

To make this behavior visible, I used a graphing tool (such as Desmos or another plotting environment) and plotted:

- The original function \( f(x) \)
- Several Taylor polynomials of increasing degree (for example, degree 1, 3, 5, and 10) centered at the same point

I chose a window that shows a symmetric interval around the center (for example, from \(-3\) to \(3\) on the x axis) and plotted all curves on the same axes. The key observations from the graphs are:

- **Very close to the center**  
  All Taylor polynomials of sufficiently high degree almost lie on top of the original function. In this region, it is visually difficult to distinguish the function from its higher degree Taylor polynomials.

- **Moderate distance from the center**  
  The low degree polynomials start to peel away first. The degree 1 (linear) approximation is usually the worst, the next degree improves it, and so on. Higher degree polynomials remain accurate over a wider interval, but eventually they also deviate.

- **Far from the center**  
  The function and the Taylor polynomials can look completely different. In some cases the polynomial might grow without bound while the function stays bounded, or the polynomial might oscillate in a way the function does not. This region clearly shows the limits of Taylor approximation.

To support these observations, I include both static images and an animated visualization.

The static comparison (for a fixed set of degrees) is embedded as:

![Function vs Taylor degree 1, 3, 5, 10](images/taylor-approx-static.png)

In addition to the static plot, I created an animated GIF where the degree of the Taylor polynomial increases over time while the function stays fixed. The frames of the animation show how the polynomial gradually “locks in” to the shape of the function near the center before breaking away farther out. This animation is embedded as:

![Animated Taylor approximation](images/taylor-approximation-animation.gif)

The animation makes it easier to see that:

- Increasing the degree primarily improves the approximation near the center.
- The region where the polynomial tracks the function closely expands somewhat as the degree grows.
- No matter how high the degree is, once we move far enough from the center, the polynomial and the function eventually separate.

### 3.3 Error and the remainder term

The graphs give an intuitive sense of how close the Taylor polynomial is to the original function, but in analysis we want a more precise way to talk about this difference. For a fixed degree \( n \), the difference between the true function and the \( n \)th degree Taylor polynomial is called the remainder or error term.

If \( T_n(x) \) denotes the Taylor polynomial of degree \( n \) for \( f(x) \) centered at some point \( a \), then the error at a point \( x \) is

\[
\text{Error}(x) = f(x) - T_n(x).
\]

Instead of just saying “the graphs look close,” we want to know how large this error can be. There is a general expression (often called the Lagrange form of the remainder) that bounds the error using:

- The next derivative of the function (the derivative of order \( n + 1 \))
- The distance between \( x \) and the center \( a \)
- A factorial term \((n+1)!\) in the denominator

The important qualitative facts are:

- For a fixed \( x \), if we increase the degree \( n \), the size of the error term typically decreases, as long as we stay inside the radius of convergence.
- For a fixed degree \( n \), if we move \( x \) closer to the center \( a \), the error becomes smaller. This matches the idea that Taylor polynomials give the best approximation near the center point where they are constructed.
- Outside the radius of convergence, even if we increase \( n \), the Taylor polynomials do not necessarily approximate the function at all; the error does not go to zero.

These observations connect the visual behavior from the graphs with the theoretical concept of error. Near the center and inside the interval of convergence, increasing the degree makes the error small, which is why the graphs almost overlap. Outside that interval, the error does not vanish, which explains why the polynomial and the original function can look completely different there.

In the rest of the project, I will use these ideas about visualization and error to look more closely at where Taylor series succeed, where they fail, and how the radius of convergence limits their usefulness.

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
