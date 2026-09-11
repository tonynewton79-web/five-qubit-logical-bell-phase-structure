# Five-Qubit Logical Bell Measurements under Photon Erasure

Exact reproducibility package for:

**Static-to-Adaptive Phase Structure of Five-Qubit Logical Bell Measurements under Photon Erasure**  
*Exact \(q=2/3\) Basis Switching, Feedforward Optimality, and Failure-Record Gauge Equivalence*

Author: **Tony Newton**  
Newton Astro Labs, London, UK

## What this repository verifies

For the non-CSS five-qubit \([[5,1,3]]\) perfect code, within transversal ancilla-free \(X/Y/Z\)-guaranteed physical Bell measurements and independent heralded photon erasure, the accompanying verifier reconstructs and checks the main results from scratch using exact rational arithmetic.

The verified results are:

1. **Static four-class collapse.** All \(6^5=7776\) static analyzer schemes collapse to exactly four loss-response classes with multiplicities
   \[
   576,\ 5760,\ 720,\ 720.
   \]

2. **Exact static basis transition.** The two envelope branches satisfy
   \[
   P_H(q)-P_L(q)=\frac{7}{32}q^4(3q-2),
   \]
   so the unique nontrivial switch is
   \[
   q_c=\frac23,
   \]
   equivalently \(\eta_c=\sqrt{2/3}\) for independent single-photon survival \(\eta\) with \(q=\eta^2\).

3. **Normalizer characterization.** The 576 high-survival schemes are exactly the 18 full-support nontrivial logical-Pauli representatives in the five-qubit normalizer, multiplied by the 32 choices of resolved Bell half.

4. **Exact adaptive Bellman problem.** The reachable adaptive information graph contains
   \[
   49\,312
   \]
   states, including
   \[
   36\,941
   \]
   nonterminal states and
   \[
   313\,200
   \]
   candidate action comparisons.

5. **Global adaptive optimum.**
   \[
   P^\star_{\rm ad}(q)=\frac54q^3+\frac74q^4-\frac{65}{32}q^5.
   \]
   Its survivor-sector probabilities are
   \[
   (s_0,\ldots,s_5)=\left(0,0,0,\frac18,\frac{17}{20},\frac{31}{32}\right).
   \]

6. **One policy is optimal on the full interval.** All 313,200 Bellman action gaps reduce to only 12 exact nonnegative polynomial forms on \(0\le q\le1\).

7. **Adaptivity removes the static boundary.**
   \[
   P^\star_{\rm ad}(q)>P^\star_{\rm static}(q),\qquad 0<q<1.
   \]

8. **Failure-record gauge equivalence.** Across all
   \[
   7^5=16\,807
   \]
   erasure/success/failure geometries, retaining the complete local failure-sign record never changes logical Bell identifiability. The verifier also checks explicit stabilizer witnesses for the doubled-stabilizer gauge argument.

## The three files

This repository intentionally contains only three files:

- `README.md` — scope, theorem statements, prior-art boundary, and instructions.
- `verify_all.py` — one self-contained Python verifier for the static theorem, adaptive theorem, and full failure-record gauge theorem.
- `paper.pdf` — the full manuscript.

## Requirements

Only standard Python is required.

Recommended:

```text
Python 3.10+
```

No NumPy, SciPy, SymPy, Qiskit, or external solver is required.

## Run all exact tests

```bash
python verify_all.py
```

The script performs three independent suites:

```text
[1/3] static phase theorem
[2/3] adaptive Bellman theorem
[3/3] failure-record gauge theorem
```

A successful run ends with:

```text
ALL EXACT VERIFICATION TESTS PASSED
```

Typical runtime is on the order of tens of seconds on a modern laptop.

## What the code reconstructs rather than assumes

The test script does not simply substitute values into the formulas printed in the paper.

It reconstructs the 64 compatible physical Bell-parity assignments from the five-qubit stabilizer constraints; exhausts all 7,776 static schemes; independently enumerates the relevant five-qubit normalizer words; builds the reachable adaptive information graph; solves the Bellman problem at exact rational sample points; interpolates every state value as a degree-at-most-five rational polynomial; recomputes all 313,200 action gaps; and exhausts all 16,807 full/coarse failure-record geometries.

## Scope and claim boundary

The verified theorem is code-specific and resource-specific. It assumes:

- the standard \([[5,1,3]]\) five-qubit stabilizer code;
- transversal ancilla-free \(X/Y/Z\)-guaranteed physical Bell analyzers;
- independent heralded pair erasure;
- ideal operations conditional on photon arrival.

Dark counts, mode mismatch, finite indistinguishability, correlated loss, multiphoton source components, and richer optical resources are outside the theorem.

The work is complementary to, rather than a replacement for, established general results on linear-optical Bell limits and loss thresholds. It is motivated in part by the 2026 logical Bell-state measurement experiment of S. Kumar, S. D. Reiss, P. van Loock, and S. Barz, while addressing a distinct finite-erasure optimization problem for the distance-three non-CSS five-qubit code.

10.5281/zenodo.22712593

## Reproducibility philosophy

The public verifier is deliberately small, readable, and exact. The key claims are checked with integer arithmetic, finite-field logic, bit masks, and Python's `fractions.Fraction`. No hidden data files are needed.
