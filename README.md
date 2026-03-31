<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jun Yi | Math Research</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Georgia', serif;
            line-height: 1.7;
            color: #2c2c2c;
            background: #fafafa;
            max-width: 780px;
            margin: 0 auto;
            padding: 40px 24px;
        }
        header {
            margin-bottom: 48px;
            padding-bottom: 24px;
            border-bottom: 2px solid #1a1a1a;
        }
        h1 {
            font-size: 28px;
            font-weight: 700;
            letter-spacing: -0.5px;
            margin-bottom: 8px;
        }
        header p {
            font-size: 15px;
            color: #555;
        }
        header p a {
            color: #555;
            text-decoration: none;
            border-bottom: 1px solid #aaa;
        }
        header p a:hover {
            color: #1a1a1a;
            border-bottom-color: #1a1a1a;
        }
        h2 {
            font-size: 20px;
            font-weight: 700;
            margin-top: 40px;
            margin-bottom: 16px;
            color: #1a1a1a;
        }
        p { margin-bottom: 14px; font-size: 16px; }
        .project {
            margin-bottom: 32px;
            padding: 20px 24px;
            background: #fff;
            border: 1px solid #e0e0e0;
            border-radius: 4px;
        }
        .project h3 {
            font-size: 17px;
            font-weight: 700;
            margin-bottom: 8px;
        }
        .project p {
            font-size: 15px;
            color: #444;
            margin-bottom: 10px;
        }
        .project a {
            font-size: 14px;
            color: #1a5276;
            text-decoration: none;
            border-bottom: 1px solid #aec6cf;
        }
        .project a:hover {
            color: #0d3b54;
            border-bottom-color: #0d3b54;
        }
        .tag {
            display: inline-block;
            font-size: 12px;
            background: #eef2f5;
            color: #4a6a7a;
            padding: 2px 10px;
            border-radius: 3px;
            margin-right: 6px;
            margin-top: 8px;
        }
        .about {
            margin-top: 48px;
            padding-top: 24px;
            border-top: 1px solid #ddd;
        }
        .about p {
            font-size: 15px;
            color: #555;
        }
        footer {
            margin-top: 48px;
            padding-top: 20px;
            border-top: 1px solid #ddd;
            font-size: 13px;
            color: #999;
        }
    </style>
</head>
<body>
 
<header>
    <h1>Hyunjun (Jun) Yi</h1>
    <p>Explorations in Analytic Number Theory</p>
    <p style="margin-top: 6px;">
        <a href="https://github.com/hjyi2027/jun-yi-math-research">GitHub Repository</a>
    </p>
</header>
 
<h2>About This Work</h2>
<p>
    This site documents an ongoing independent exploration connecting calculus, infinite series, and number theory. The work began with a question: why does summing the reciprocals of perfect squares yield a result involving pi? Starting from the Basel problem and Taylor series, these investigations trace connections between classical analysis and number-theoretic identities, with a focus on the Riemann zeta function, its special values, and the combinatorial structures that underlie them.
</p>
<p>
    All work here is self-directed and conducted outside of any course or formal program.
</p>
 
<h2>Projects</h2>
 
<div class="project">
    <h3>The Basel Problem and the Riemann Zeta Function</h3>
    <p>
        Multiple approaches to evaluating &zeta;(2) = &pi;&sup2;/6, including Euler's infinite product argument. Investigation of &zeta;(2k) for positive even integers via Bernoulli numbers. Computational verification of zeta values. Analysis of the even/odd asymmetry: why every &zeta;(2k) has a closed form involving &pi;, while no odd zeta value does.
    </p>
    <span class="tag">analytic number theory</span>
    <span class="tag">zeta function</span>
    <span class="tag">Bernoulli numbers</span>
    <br><br>
    <a href="https://github.com/hjyi2027/jun-yi-math-research/blob/main/projects/basel-sum.md">Full writeup</a>
</div>
 
<div class="project">
    <h3>Computational Experiments with the Zeta Function</h3>
    <p>
        Python scripts for numerically investigating convergence rates of &zeta;(s) partial sums, verifying even zeta values against the Bernoulli number formula, comparing raw partial sums to Euler-Maclaurin corrected sums, and examining patterns in ratios of consecutive zeta values and odd zeta values.
    </p>
    <span class="tag">Python</span>
    <span class="tag">computational number theory</span>
    <span class="tag">Euler-Maclaurin</span>
    <br><br>
    <a href="https://github.com/hjyi2027/jun-yi-math-research/blob/main/projects/zeta-experiment.py">Code</a> &nbsp;|&nbsp;
    <a href="https://github.com/hjyi2027/jun-yi-math-research/blob/main/projects/zeta-experiment-output.txt">Output</a>
</div>
 
<div class="project">
    <h3>Taylor Series and Convergence</h3>
    <p>
        Foundations of power series approximation. Visualizations of Taylor polynomial convergence for e<sup>x</sup>, sin(x), and ln(1+x). Analysis of radius of convergence, the distinction between smooth and analytic functions, and pathological cases where Taylor series converge but fail to represent the function.
    </p>
    <span class="tag">analysis</span>
    <span class="tag">approximation theory</span>
    <span class="tag">convergence</span>
    <br><br>
    <a href="https://github.com/hjyi2027/jun-yi-math-research/blob/main/projects/taylor-series-and-convergence.md">Full writeup</a>
</div>
 
<div class="project">
    <h3>Open Questions and Future Directions</h3>
    <p>
        Problems and patterns encountered during this exploration that remain unresolved. Includes questions about the even/odd zeta asymmetry, convergence acceleration via Euler-Maclaurin, the rate of approach of &zeta;(s) to 1, Bernoulli number growth, connections to the Euler product over primes, and planned investigations into Dirichlet L-functions, p-adic zeta functions, and multiple zeta values.
    </p>
    <span class="tag">open problems</span>
    <span class="tag">research directions</span>
    <br><br>
    <a href="https://github.com/hjyi2027/jun-yi-math-research/blob/main/projects/open-questions.md">Full document</a>
</div>
 
<div class="about">
    <h2>Background</h2>
    <p>
        I am a junior at Seoul International School. My mathematical background includes a perfect score on the AMC-12, coursework in multivariable calculus and linear algebra from Stanford University, and two summers at the AwesomeMath Summer Program. I currently lead a competitive math team of USAMO Honourable Mentions and IMO medalists researching in various mathematical topics and competing in various online math competitions.
    </p>
    <p style="margin-top: 12px;">
        I am currently seeking research mentorship in analytic number theory, particularly in areas related to integer partitions, q-series, and special values of L-functions.
    </p>
</div>
 
<footer>
    Hyunjun (Jun) Yi &nbsp;|&nbsp; Seoul International School &nbsp;|&nbsp; 
    <a href="https://github.com/hjyi2027/jun-yi-math-research" style="color: #999; text-decoration: none; border-bottom: 1px solid #ccc;">GitHub</a>
</footer>
 
</body>
</html>
