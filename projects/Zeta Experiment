"""
Computational experiments with the Riemann zeta function.

This script investigates:
1. Numerical verification of zeta(2k) = rational * pi^(2k)
2. Convergence rates of partial sums
3. Patterns in ratios of consecutive zeta values
4. Bernoulli number extraction from zeta values
5. Comparison of series acceleration techniques

Author: Jun Yi
"""

import math
from fractions import Fraction


# ============================================================
# 1. Computing zeta(s) via partial sums
# ============================================================

def zeta_partial_sum(s, N):
    """Compute the partial sum of zeta(s) using the first N terms."""
    return sum(1.0 / n**s for n in range(1, N + 1))


def zeta_error_bound(s, N):
    """Upper bound on the tail sum_{n=N+1}^{infty} 1/n^s via integral comparison."""
    if s <= 1:
        return float('inf')
    return N**(1 - s) / (s - 1)


# ============================================================
# 2. Known closed forms for even zeta values
# ============================================================

# zeta(2k) = (-1)^(k+1) * (2*pi)^(2k) * B_{2k} / (2 * (2k)!)
# First several Bernoulli numbers B_{2k}:
BERNOULLI = {
    2: Fraction(1, 6),
    4: Fraction(-1, 30),
    6: Fraction(1, 42),
    8: Fraction(-1, 30),
    10: Fraction(5, 66),
    12: Fraction(-691, 2730),
    14: Fraction(7, 6),
}

def zeta_even_exact(k):
    """Compute zeta(2k) using Bernoulli numbers. Returns (rational_part, power_of_pi)."""
    B = BERNOULLI.get(2 * k)
    if B is None:
        return None
    sign = (-1)**(k + 1)
    numerator = sign * (2**(2*k)) * B
    denominator = Fraction(2) * Fraction(math.factorial(2 * k))
    rational_part = numerator / denominator
    return rational_part  # multiply by pi^(2k) to get zeta(2k)


def zeta_even_numerical(k):
    """Compute zeta(2k) numerically from the Bernoulli number formula."""
    rational = zeta_even_exact(k)
    if rational is None:
        return None
    return float(rational) * math.pi**(2 * k)


# ============================================================
# 3. Convergence rate analysis
# ============================================================

def convergence_analysis(s_values, N_values):
    """For each s, compute partial sums at various N and measure error."""
    print(f"{'s':<6} {'N':<10} {'Partial Sum':<20} {'Error Bound':<15} {'Actual Error':<15}")
    print("-" * 70)

    for s in s_values:
        # Use a very large partial sum as "true" value
        true_val = zeta_partial_sum(s, 100000)
        for N in N_values:
            partial = zeta_partial_sum(s, N)
            bound = zeta_error_bound(s, N)
            actual_err = abs(true_val - partial)
            print(f"{s:<6} {N:<10} {partial:<20.12f} {bound:<15.8f} {actual_err:<15.8f}")
        print()


# ============================================================
# 4. Ratios of consecutive even zeta values
# ============================================================

def zeta_ratios():
    """Compute zeta(2k) / zeta(2k+2) for small k."""
    print("Ratios zeta(2k) / zeta(2k+2):")
    print(f"{'k':<6} {'zeta(2k)':<20} {'zeta(2k+2)':<20} {'Ratio':<15}")
    print("-" * 65)

    N = 100000  # large partial sum for accuracy
    for k in range(1, 8):
        z_2k = zeta_partial_sum(2 * k, N)
        z_2k2 = zeta_partial_sum(2 * k + 2, N)
        ratio = z_2k / z_2k2
        print(f"{k:<6} {z_2k:<20.12f} {z_2k2:<20.12f} {ratio:<15.8f}")


# ============================================================
# 5. Odd zeta values (no known closed form)
# ============================================================

def odd_zeta_values():
    """Compute odd zeta values and look for patterns."""
    print("Odd zeta values (no known closed form in terms of pi):")
    print(f"{'s':<6} {'zeta(s)':<25} {'zeta(s)/pi^s':<20}")
    print("-" * 55)

    N = 100000
    for s in [3, 5, 7, 9, 11]:
        z = zeta_partial_sum(s, N)
        ratio = z / math.pi**s
        print(f"{s:<6} {z:<25.15f} {ratio:<20.15f}")

    print("\nNote: unlike even values, these ratios do not appear to be")
    print("simple rational numbers, consistent with the conjecture that")
    print("odd zeta values have no closed form involving pi.")


# ============================================================
# 6. Verifying even zeta values against Bernoulli formula
# ============================================================

def verify_even_zeta():
    """Compare partial sum approximations to exact Bernoulli formula values."""
    print("Verification: partial sums vs Bernoulli formula for zeta(2k)")
    print(f"{'2k':<6} {'Partial Sum (N=10^5)':<25} {'Bernoulli Formula':<25} {'Difference':<15}")
    print("-" * 75)

    N = 100000
    for k in range(1, 7):
        partial = zeta_partial_sum(2 * k, N)
        exact = zeta_even_numerical(k)
        if exact is not None:
            diff = abs(partial - exact)
            print(f"{2*k:<6} {partial:<25.15f} {exact:<25.15f} {diff:<15.2e}")


# ============================================================
# 7. Euler-Maclaurin correction for better partial sums
# ============================================================

def zeta_euler_maclaurin(s, N):
    """
    Compute zeta(s) using partial sum + integral correction + first Bernoulli correction.
    
    zeta(s) approx sum_{n=1}^{N} 1/n^s + N^{1-s}/(s-1) + (1/2)*N^{-s}
    
    This gives a much better approximation than the raw partial sum.
    """
    partial = zeta_partial_sum(s, N)
    integral_correction = N**(1 - s) / (s - 1)
    bernoulli_correction = 0.5 * N**(-s)
    return partial + integral_correction + bernoulli_correction


def compare_methods():
    """Compare raw partial sum vs Euler-Maclaurin corrected sum."""
    print("Raw partial sum vs Euler-Maclaurin corrected (s=2, true value = pi^2/6):")
    true_val = math.pi**2 / 6
    print(f"{'N':<10} {'Raw Sum':<20} {'Raw Error':<15} {'E-M Corrected':<20} {'E-M Error':<15}")
    print("-" * 80)

    for N in [10, 50, 100, 500, 1000, 5000]:
        raw = zeta_partial_sum(2, N)
        em = zeta_euler_maclaurin(2, N)
        print(f"{N:<10} {raw:<20.12f} {abs(raw-true_val):<15.8f} {em:<20.12f} {abs(em-true_val):<15.8f}")


# ============================================================
# Main
# ============================================================

if __name__ == "__main__":
    print("=" * 75)
    print("COMPUTATIONAL EXPERIMENTS WITH THE RIEMANN ZETA FUNCTION")
    print("=" * 75)
    print()

    print("--- 1. Convergence Rate Analysis ---")
    convergence_analysis(
        s_values=[2, 4, 6, 10],
        N_values=[10, 100, 1000, 10000]
    )

    print("--- 2. Even Zeta Value Verification ---")
    verify_even_zeta()
    print()

    print("--- 3. Ratios of Consecutive Even Zeta Values ---")
    zeta_ratios()
    print()

    print("--- 4. Odd Zeta Values ---")
    odd_zeta_values()
    print()

    print("--- 5. Partial Sum vs Euler-Maclaurin Comparison ---")
    compare_methods()
    print()

    # Print the exact rational parts for reference
    print("--- 6. Exact Rational Prefactors for zeta(2k)/pi^(2k) ---")
    for k in range(1, 7):
        r = zeta_even_exact(k)
        if r is not None:
            print(f"  zeta({2*k}) = ({r}) * pi^{2*k} = {float(r) * math.pi**(2*k):.15f}")
