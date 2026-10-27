# ECE 2112: Advanced Computer Programming and Algorithms
## Experiment 5: Introduction to MATLAB Programming

**Name:** Villaluna, Dirk Lendl E.
**Section:** 2ECE-A
**Course & Department:** Electronics Engineering Department, Faculty of Engineering, University of Santo Tomas  
**Date Submitted:** October 2026  

---

## I. Overview & Objectives

This laboratory activity demonstrates fundamental MATLAB matrix manipulations, complex array behaviors, and techniques for solving simultaneous systems of linear equations.

The key objectives include:
1. Creating and indexing real and complex matrices in MATLAB.
2. Distinguishing standard transpose (`transpose(A)`, `A.'`) from the complex-conjugate transpose (`A'`).
3. Expressing simultaneous linear systems in standard matrix form (Ax = b).
4. Solving linear systems via the Inverse Method and Cramer's Rule, followed by residual and error norm validation.

---

## II. Programming Problems Summary

### Problem A: Transpose Operations
The script defines a real matrix R (3 × 4) and a complex matrix Z (2 × 3):
- Computes `transpose(A)`, `A'`, and `A.'` for both matrices.
- Analyzes the mathematical and functional differences between each transpose operator:
  - **Real Matrix R:** All three operations (`transpose(R)`, `R'`, and `R.'`) produce identical results because conjugating real numbers leaves them unchanged.
  - **Complex Matrix Z:** `transpose(Z)` and `Z.'` produce identical results as both perform non-conjugate transposition (swapping row and column indices).
  - **Apostrophe Operator (`'`):** When applied to complex entries, it computes the **Hermitian transpose** (complex-conjugate transpose), interchanging rows and columns while simultaneously negating the sign of the imaginary components.

---

### Problem B: Solving a Linear System (Ax = b)

The following 4 × 4 system of simultaneous linear equations is solved:

$$2x_1 - x_2 + 3x_3 + 2x_4 = 16$$
$$x_1 + 4x_2 - 2x_3 + x_4 = -7$$
$$3x_1 + 2x_2 + x_3 - x_4 = 6$$
$$-2x_1 + 3x_2 + 4x_3 + 2x_4 = 7$$

#### 1. Inverse Method
Computed using MATLAB's built-in `inv()` function:
$$x_{\text{inv}} = A^{-1} b$$

#### 2. Cramer's Rule
Computed by substituting vector b into column i of matrix A (yielding A_i) and taking determinants:
$$x_i = \frac{\det(A_i)}{\det(A)}$$
Implemented cleanly using a `for` loop over i = 1 to 4.

#### 3. Numerical Verification & Checks
- **Determinant Check:** det(A) = 280 ≠ 0, confirming the system has a unique solution.
- **Consistency Check:** norm(x_inv - x_cramer) ≈ 0 (verified within numerical precision: ≈ 2.39 × 10⁻¹⁵).
- **Residual Check:** norm(A * x_inv - b) ≈ 0 (verified within numerical precision: ≈ 8.88 × 10⁻¹⁶).

**Expected Solution Vector:**
$$x = \begin{bmatrix} 2 \\ -1 \\ 3 \\ 1 \end{bmatrix}$$

---

## Thank you for reading. The MATLAB file can be found
