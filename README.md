# ECE2112-PA5 | Dirk Lendl E. Villaluna | 2ECE-A

# Overview
This repository contains the completed Programming Assignment 5 for the course ECE2112 - Advanced Computer Programming and Algorithms for the Academic Year 2026-27. The topic coverage of the said programming assignment is Introduction to MATLAB Programming, focusing on matrix definitions, transpose operations, and solving simultaneous linear equations using the Inverse Method and Cramer's Rule.

## A. TRANSPOSE OPERATIONS

Define a real matrix R (3x4) and a complex matrix Z (2x3). For each matrix, compute and display its transpose using the built-in function transpose(), the conjugate transpose operator ('), and the non-conjugate transpose operator (.'). Answer the conceptual questions regarding their behavior as inline comments.

Requirements to follow:
1. Define matrices R and Z exactly as specified.
2. Compute and display transpose(A), A', and A.' for both matrices.
3. Include comments explaining which operations yield identical results and the role of the apostrophe operator on complex entries.

Methods & Functions Used:
- transpose(A): Built-in MATLAB function that performs standard transposition (swapping rows and columns without conjugating complex numbers).
- A': Complex-conjugate transpose (Hermitian transpose) operator.
- A.': Array transpose operator that flips rows and columns without conjugating complex elements.
- disp(): Displays labels and matrix outputs cleanly in the Command Window.

Implementation of code:

```
R = [5 -2 0 7; 1 3 -4 2;6 0 8 -1]; 
Z = [2+3i -1+4i 5-2i; -3+i 6 2+5i];

transpose(R)

ans =

     5     1     6
    -2     3     0
     0    -4     8
     7     2    -1

>> R'

ans =

     5     1     6
    -2     3     0
     0    -4     8
     7     2    -1

>> R.'

ans =

     5     1     6
    -2     3     0
     0    -4     8
     7     2    -1

>> transpose(Z)

ans =

   2.0000 + 3.0000i   1.0000 + 0.0000i
  -1.0000 + 4.0000i   6.0000 + 0.0000i
   5.0000 - 2.0000i   2.0000 + 5.0000i

>> Z'

ans =

   2.0000 - 3.0000i   1.0000 + 0.0000i
  -1.0000 - 4.0000i   6.0000 + 0.0000i
   5.0000 + 2.0000i   2.0000 - 5.0000i

>> Z.'

ans =

   2.0000 + 3.0000i   1.0000 + 0.0000i
  -1.0000 + 4.0000i   6.0000 + 0.0000i
   5.0000 - 2.0000i   2.0000 + 5.0000i

>> % a. All three operations gave the same results for the real matrix R.
% b. Only the operations transpose(Z) and Z.' gave identical results for the complex matrix Z.
% c. The apostrophe operator (') performs a complex-conjugate 
%    transpose. Additionally, it conjugates every entry by negating the sign of its 
%    imaginary component.
```

## B. TWO METHODS FOR A LINEAR SYSTEM

Set up the coefficient matrix A and constant vector b for the given 4x4 simultaneous linear system. Solve for the unknowns using two approaches: the Inverse Method and Cramer's Rule. Validate the results by evaluating determinants and numerical error norms.

Requirements to follow:
1. Create the coefficient matrix A and right-hand-side column vector b.
2. Solve using the Inverse Method (inv(A) * b) without using the left-division operator (\).
3. Solve using Cramer's Rule by iteratively replacing columns of A with vector b and computing determinants.
4. Display det(A), x_inv, x_cramer, norm(x_inv - x_cramer), and norm(A * x_inv - b). Both norm values must be approximately zero.

Methods & Functions Used:
- inv(A): Computes the matrix inverse of A.
- det(A): Evaluates the determinant of a square matrix.
- zeros(n, 1): Pre-allocates memory for the solution column vector.
- for loop: Iterates through each column index to replace columns of A with vector b for Cramer's Rule.
- norm(): Computes the Euclidean vector norm to confirm consistency and residual error precision.
- disp(): Displays certain text and results, depending on the variable inside the parentheses.

Implementation of code:

```
% B. TWO METHODS FOR A LINEAR SYSTEM

%    2*x1 -   x2 + 3*x3 + 2*x4 = 16
%      x1 + 4*x2 - 2*x3 +   x4 = -7
%    3*x1 + 2*x2 +   x3 -   x4 =  6
%   -2*x1 + 3*x2 + 4*x3 + 2*x4 =  7

A = [2 -1 3 2; 1 4 -2 1; 3 2 1 -1; -2 3 4 2]; 
b = [16; -7; 6; 7];

x_inv = inv(A) * b

x_inv =

    2.0000
   -1.0000
    3.0000
    1.0000

>> det_A = det(A);

n = length(b);
x_cramer = zeros(n, 1);

for i = 1:n;
A_temp = A;
A_temp(:, i) = b;
x_cramer(i) = det(A_temp)/det_A;
end
>>  disp('---Problem B Checks & Displays---');
disp('det_A');
disp(det(A));

disp('x_inv:');
disp(x_inv);

disp('x_cramer:');
disp(x_cramer);

disp('norm(x_inv - x_cramer):');
disp(norm(x_inv - x_cramer));

disp('norm(A * x_inv - b):');
disp(norm(A * x_inv - b));
---Problem B Checks & Displays---
det_A
   280

x_inv:
    2.0000
   -1.0000
    3.0000
    1.0000

x_cramer:
    2.0000
   -1.0000
    3.0000
    1.0000

norm(x_inv - x_cramer):
   7.6919e-16

norm(A * x_inv - b):
   4.3512e-15
```

## And with that, THANK YOU FOR READING! :D
# To view the actual implementation in MATLAB, kindly download the .m file included in this repository.
