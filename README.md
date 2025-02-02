
# The Hidden Geometry of Singular and Scaled Matrices: Why Visually Different Matrices Behave the Same

## Introduction
In linear algebra, singular matrices are known for their collapse of dimensions and inability to uniquely invert them due to linearly dependent rows or columns. What is less understood, however, is how singular matrices behave when **scaled** or **slightly modified** by adjusting their diagonal elements. Although these adjustments can make the matrices look visually different, their underlying behavior often remains the same due to the way **eigenvalues and eigenvectors govern matrix transformations.**

This paper explores how scaling and small adjustments to the diagonal elements of singular matrices produce **similar transformations** and how their shared eigenstructure explains this phenomenon. We provide intuitive examples and a numerical demonstration to highlight why matrices that look dissimilar often exhibit **the same behavior in both forward and inverse transformations**.

---

## Singular Matrices and Their Unique Properties
A matrix $A$ is considered **singular** if its determinant is zero:

$$
\det(A) = 0
$$

This condition arises when the matrix has **linearly dependent rows or columns**, causing it to lose rank and project input vectors onto a **lower-dimensional subspace**. Singular matrices are important because they **collapse input vectors along a specific direction, known as the null space.** The eigenvalue corresponding to this direction is zero.

Consider the singular matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
2 & 4
\end{bmatrix}
$$

This matrix is singular because the second row is twice the first row, making it rank-deficient. Its eigenvalues can be found by solving:

$$
\det(A - \lambda I) = 0
$$

The eigenvalues of $A$ are $\lambda_1 = 0$ and $\lambda_2 = 5$, indicating that the matrix **collapses vectors along the eigenvector corresponding to $\lambda_1 = 0$** (the null space).

---

## Scaling the Singular Matrix
Scaling a singular matrix by a constant $c$ results in:

$$
cA = \begin{bmatrix}
c & 2c \\
2c & 4c
\end{bmatrix}
$$

Although the entries of the matrix are multiplied by $c$, the **eigenvectors remain unchanged**, and the eigenvalues are scaled proportionally:

$$
\lambda_i(cA) = c \cdot \lambda_i(A)
$$

Thus, the eigenvalue corresponding to the null space direction remains zero, while the nonzero eigenvalue is scaled by $c$. This proportional scaling preserves the **geometric behavior** of the matrix.

For example, if $A \mathbf{x} = \mathbf{0}$ for some nonzero vector $\mathbf{x}$ (i.e., the null space), then:

$$
cA \mathbf{x} = c \cdot \mathbf{0} = \mathbf{0}
$$

This shows that **the scaling factor does not affect the fundamental collapse of input vectors along the null space direction**.

---

## Modifying the Diagonal Elements
To make a singular matrix **invertible** or to examine how small changes affect its behavior, we can **slightly modify its diagonal elements.** This means adding a small value $\epsilon$ to the diagonal, which shifts the eigenvalues away from zero. Consider the modified matrix:

$$
A' = \begin{bmatrix}
1 + \epsilon & 2 \\
2 & 4 + \epsilon
\end{bmatrix}
$$

The adjustment to the diagonal elements **prevents the complete collapse** of input vectors, making the matrix invertible. The eigenvalues of the modified matrix are approximately:

$$
\lambda'_1 \approx \epsilon \quad \text{and} \quad \lambda'_2 \approx 5 + \epsilon
$$

Similarly, for the scaled matrix $cA$, we modify the diagonal elements:

$$
(cA)' = \begin{bmatrix}
c + \epsilon & 2c \\
2c & 4c + \epsilon
\end{bmatrix}
$$

Even though these matrices **look different numerically**, they behave similarly because the **relative change in eigenvalues is proportional**.

---

## Why These Matrices Behave Similarly

### 1. **Eigenvectors Are Unchanged**
The eigenvectors of both $A'$ and $(cA)'$ remain aligned with the original matrix $A$ because **scaling and small changes to the diagonal do not alter their directions**. Thus, input vectors are still projected along the same geometric directions.

### 2. **Proportional Scaling of Eigenvalues**
The eigenvalues of $(cA)'$ are scaled by $c$ and shifted by $\epsilon$, but this scaling is proportional:

$$
\lambda'_i((cA)') \approx c \lambda'_i(A')
$$

This proportional relationship means that the **forward transformation projects input vectors similarly**, and the inverse transformation exhibits similar expansion or contraction behavior.

---

## Forward and Inverse Transformation Comparison

### **Forward Transformation**
The forward transformation $A' \mathbf{x} = \mathbf{b}$ projects input vectors along the eigenvector directions. Input vectors aligned with the null space direction produce **small output values** because the corresponding eigenvalue $\lambda'_1 \approx \epsilon$ is small.

For example:

$$
A' \begin{bmatrix} 1 \\ -1 \end{bmatrix} = \begin{bmatrix} 0 \\ -3 \end{bmatrix}
\quad \text{and} \quad (cA)' \begin{bmatrix} 1 \\ -1 \end{bmatrix} = \begin{bmatrix} 0 \\ -30 \end{bmatrix}
$$

Although the outputs differ in magnitude, they **maintain the same directional behavior**.

### **Inverse Transformation**
The inverse transformation $A'^{-1} \mathbf{b} = \mathbf{x}$ depends on the **smallest eigenvalue** $\lambda'_1$. When $\epsilon$ is small, the inverse transformation **amplifies small output values, causing large inputs**:

$$
A'^{-1} \approx \begin{bmatrix}
\frac{1}{\epsilon} & \dots \\
\dots & \dots
\end{bmatrix}
$$

Thus, even though $A'$ and $(cA)'$ differ numerically, they both exhibit **similar instability** when the output $\mathbf{b}$ has components along the near-null space direction.

---

## Numerical Example
Consider the singular matrix:

$$
A = \begin{bmatrix}
1 & 2 \\
2 & 4
\end{bmatrix}
\quad \text{and} \quad 10A = \begin{bmatrix}
10 & 20 \\
20 & 40
\end{bmatrix}
$$

Modify the diagonal elements:

$$
A' = \begin{bmatrix}
2 & 2 \\
2 & 5
\end{bmatrix}
\quad \text{and} \quad (10A)' = \begin{bmatrix}
11 & 20 \\
20 & 41
\end{bmatrix}
$$

Despite the numerical differences, both matrices **project input vectors and expand inputs during inversion in the same way**.

---

## Conclusion
The behavior of singular and near-singular matrices is largely determined by their **eigenstructure, not their individual entries.** Scaling and modifying the diagonal elements may change the appearance of the matrix, but their **eigenvectors remain aligned**, and their eigenvalues shift in a proportional manner. This hidden geometric relationship explains why matrices that appear numerically dissimilar often exhibit **the same behavior** in both forward and inverse transformations.

Understanding this relationship is crucial in **numerical analysis and optimization**, particularly in handling ill-conditioned systems where small changes can lead to large instabilities.
