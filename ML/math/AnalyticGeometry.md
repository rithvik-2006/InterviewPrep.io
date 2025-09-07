
**Chapter 3: Analytic Geometry – Geometric Interpretation and Intuition for Machine Learning**

Analytic geometry provides a **geometric interpretation and intuition** to the abstract concepts of vectors, vector spaces, and linear mappings introduced in linear algebra. This chapter focuses on equipping vector spaces with an **inner product** to define fundamental geometric properties like **length, distance, and angles** between vectors. These concepts are crucial for understanding **similarity and distances** in data, which are then used in various machine learning algorithms.

**Key Concepts and Their Importance:**

*   **Inner products and their corresponding norms and metrics** capture intuitive notions of similarity and distances, which are foundational for developing methods like the **Support Vector Machine (SVM)** (Chapter 12).
*   Concepts of **lengths and angles** between vectors are used to discuss **orthogonal projections**, which are central to **Principal Component Analysis (PCA)** (Chapter 10) and **linear regression** (Chapter 9).

---

### **1. Norms**

A **norm** quantifies the "length" or "magnitude" of a vector.

*   **Definition**: A function $|| \cdot || : V \to \mathbb{R}$ that assigns each vector $x \in V$ its length $||x|| \in \mathbb{R}$, satisfying three properties for all $\lambda \in \mathbb{R}$ and $x, y \in V$:
    1.  **Absolutely homogeneous**: $|| \lambda x || = |\lambda| ||x||$.
    2.  **Triangle inequality**: $||x + y|| \le ||x|| + ||y||$ (geometrically, the sum of any two sides of a triangle must be greater than or equal to the length of the third side).
    3.  **Positive definite**: $||x|| \ge 0$ and $||x|| = 0 \Leftrightarrow x = 0$.
*   The book primarily considers **finite-dimensional vector spaces** $\mathbb{R}^n$.

**Examples of Norms:**

*   **Manhattan Norm (ℓ1 norm)**: $||x||_1 := \sum_{i=1}^n |x_i|$. In $\mathbb{R}^2$, vectors with $||x||_1 = 1$ form a square rotated by 45 degrees [113, Figure 3.3].
*   **Euclidean Norm (ℓ2 norm)**: $||x||_2 := \sqrt{\sum_{i=1}^n x_i^2} = \sqrt{x^\top x}$. This computes the Euclidean distance of $x$ from the origin. In $\mathbb{R}^2$, vectors with $||x||_2 = 1$ form a circle [114, Figure 3.3].
*   **Default Norm**: Throughout the book, the **Euclidean norm ($|| \cdot ||_2$)** is used by default unless specified otherwise.

---

### **2. Inner Products**

Inner products allow for the introduction of intuitive geometrical concepts and are primarily used to determine **orthogonality**.

*   **Dot Product**: A familiar type of inner product in $\mathbb{R}^n$, defined as $x^\top y = \sum_{i=1}^n x_i y_i$.
*   **Bilinear Mapping**: A mapping $\Omega: V \times V \to \mathbb{R}$ is bilinear if it is linear in each argument.
    *   $\Omega(\lambda x + \psi y, z) = \lambda \Omega(x, z) + \psi \Omega(y, z)$.
    *   $\Omega(x, \lambda y + \psi z) = \lambda \Omega(x, y) + \psi \Omega(x, z)$.
*   **Properties of Bilinear Mappings**:
    *   **Symmetric**: $\Omega(x, y) = \Omega(y, x)$ for all $x, y \in V$ (order of arguments doesn't matter).
    *   **Positive Definite**: $\forall x \in V \setminus \{0\} : \Omega(x, x) > 0$, and $\Omega(0, 0) = 0$.
*   **Definition of an Inner Product**: A **positive definite, symmetric bilinear mapping** $\Omega: V \times V \to \mathbb{R}$ is called an **inner product** on $V$. It is typically denoted by $\langle x, y \rangle$.
*   **Inner Product Space**: A pair $(V, \langle \cdot, \cdot \rangle)$ is called an **inner product space** or (real) **vector space with inner product**. If the dot product is used, it's called a **Euclidean vector space**.

**Example**: An inner product in $\mathbb{R}^2$ different from the dot product: $\langle x, y \rangle := x_1 y_1 - (x_1 y_2 + x_2 y_1) + 2x_2 y_2$.

---

### **3. Symmetric, Positive Definite Matrices**

These matrices are important in machine learning and are defined via the inner product.

*   **Definition**: A symmetric matrix $A \in \mathbb{R}^{n \times n}$ is called **symmetric, positive definite** (or just positive definite) if $\forall x \in V \setminus \{0\} : x^\top A x > 0$.
    *   If $x^\top A x \ge 0$, it's called **symmetric, positive semidefinite**.
*   **Connection to Inner Products**: If $A \in \mathbb{R}^{n \times n}$ is symmetric and positive definite, then $\langle x, y \rangle = \hat{x}^\top A \hat{y}$ defines an inner product, where $\hat{x}, \hat{y}$ are coordinate representations with respect to an ordered basis. This holds if and only if such a matrix $A$ exists for an inner product.
*   **Properties**: If $A$ is symmetric, positive definite:
    *   Its **null space (kernel)** consists only of 0, implying $Ax \neq 0$ if $x \neq 0$.
    *   Its **diagonal elements $a_{ii}$ are positive**.

---

### **4. Lengths and Distances**

*   **Inner Products Induce Norms**: Any inner product naturally induces a norm: $||x|| := \sqrt{\langle x, x \rangle}$. However, not every norm is induced by an inner product (e.g., Manhattan norm).
*   **Cauchy-Schwarz Inequality**: For an inner product vector space $(V, \langle \cdot, \cdot \rangle)$, the induced norm $|| \cdot ||$ satisfies $|\langle x, y \rangle| \le ||x|| ||y||$.
*   **Distance (Metric)**: The function $d: V \times V \to \mathbb{R}$ such that $d(x, y) = ||x - y||$ is called a **metric**.
    *   **Properties of a Metric**:
        1.  **Positive definite**: $d(x, y) \ge 0$ and $d(x, y) = 0 \Leftrightarrow x = y$.
        2.  **Symmetric**: $d(x, y) = d(y, x)$.
        3.  **Triangle inequality**: $d(x, z) \le d(x, y) + d(y, z)$.
    *   **Distinction from Inner Product**: Very similar $x$ and $y$ yield a large inner product value but a small metric value.

---

### **5. Angles and Orthogonality**

*   **Angle Between Vectors**: For non-zero vectors $x, y \in V$, the angle $\omega \in [0, \pi]$ between them is defined by $\cos \omega = \frac{\langle x, y \rangle}{||x|| ||y||}$. The angle intuitively indicates the **similarity of their orientations**.
*   **Orthogonality**: Two non-zero vectors $x, y$ are **orthogonal** (denoted $x \perp y$) if their inner product is zero: $\langle x, y \rangle = 0$.
    *   The choice of inner product affects whether vectors are orthogonal.
*   **Orthogonal Matrix**: A square matrix $A \in \mathbb{R}^{n \times n}$ is an **orthogonal matrix** if and only if its columns are orthonormal, meaning $AA^\top = I = A^\top A$. This implies $A^\top = A^{-1}$.
    *   Orthogonal matrices **preserve both angles and distances**.
    *   They define transformations that are **rotations** (possibly with flips).

---

### **6. Orthonormal Basis (ONB)**

*   **Definition**: For an $n$-dimensional vector space $V$ and a basis $\{b_1, \dots, b_n\}$:
    *   It is an **orthonormal basis (ONB)** if $\langle b_i, b_j \rangle = 0$ for $i \neq j$ (orthogonality) and $\langle b_i, b_i \rangle = 1$ (unit length).
    *   If only the orthogonality condition is satisfied, it's an **orthogonal basis**.
*   **Construction**: An ONB can be constructively built from any basis using the **Gram-Schmidt process**.
*   **Example**: The canonical/standard basis in $\mathbb{R}^n$ (with dot product) is an ONB.
*   **Applications**: Orthonormal bases are exploited in **Support Vector Machines (SVMs)** (Chapter 12) and **Principal Component Analysis (PCA)** (Chapter 10).

---

### **7. Orthogonal Complement**

*   **Definition**: For an $M$-dimensional subspace $U \subseteq V$ (a $D$-dimensional vector space), its **orthogonal complement $U^\perp$** is a $(D-M)$-dimensional subspace containing all vectors in $V$ that are **orthogonal to every vector in $U$**.
*   **Properties**:
    *   $U \cap U^\perp = \{0\}$.
    *   Any vector $x \in V$ can be uniquely decomposed into $x = \sum_{m=1}^M \lambda_m b_m + \sum_{j=1}^{D-M} \psi_j b_j^\perp$.
*   **Applications**: Used to describe **planes** and **hyperplanes** in $n$-dimensional spaces using a **normal vector** (a basis vector of $U^\perp$). Plays an important role in **linear dimensionality reduction** (Chapter 10).

---

### **8. Inner Product of Functions**

The concept of an inner product can be generalized to vectors with an infinite number of entries or continuous-valued functions.

*   **Definition**: For two functions $u: \mathbb{R} \to \mathbb{R}$ and $v: \mathbb{R} \to \mathbb{R}$, an inner product can be defined as the definite integral: $\langle u, v \rangle := \int_a^b u(x)v(x)dx$.
*   **Orthogonality of Functions**: If this integral evaluates to 0, the functions $u$ and $v$ are orthogonal.
*   **Applications**: Fundamental to concepts like **Fourier series** and the inner product of **random variables** (Section 6.4.6).

---

### **9. Orthogonal Projections**

Projections are a crucial class of linear transformations, particularly in **machine learning for data compression and visualization** of high-dimensional data.

*   **Goal**: Minimize information loss when compressing data by finding informative dimensions.
*   **Definition of a Projection**: A linear mapping $\pi: V \to U$ (where $U \subseteq V$ is a subspace) is a **projection** if $\pi^2 = \pi \circ \pi = \pi$.
    *   This applies to **projection matrices $P_\pi$**, which satisfy $P_\pi^2 = P_\pi$.
*   The following derivations assume the **dot product** as the inner product.

**a. Projection onto One-Dimensional Subspaces (Lines)**

*   **Setting**: Projecting a vector $x \in \mathbb{R}^n$ onto a line (1D subspace) $U \subseteq \mathbb{R}^n$ spanned by a basis vector $b \in \mathbb{R}^n$ [144, Figure 3.10(a)].
*   **Properties of the projection $\pi_U(x)$**:
    *   It is the **closest vector in $U$ to $x$**, minimizing $||x - \pi_U(x)||$.
    *   The segment $x - \pi_U(x)$ is **orthogonal to $U$** (and thus to $b$).
*   **Derivation**:
    1.  **Find Coordinate $\lambda$**: Since $\pi_U(x) = \lambda b$, the orthogonality condition $\langle \pi_U(x) - x, b \rangle = 0$ leads to $\lambda = \frac{\langle x, b \rangle}{||b||^2}$. If $||b|| = 1$, then $\lambda = b^\top x$.
    2.  **Find Projection Point $\pi_U(x)$**: $\pi_U(x) = \frac{\langle x, b \rangle}{||b||^2} b$.
    3.  **Find Projection Matrix $P_\pi$**: Since $\pi_U(x)$ is a linear mapping, $P_\pi x = \pi_U(x)$. For the dot product, $P_\pi = \frac{bb^\top}{b^\top b}$.
*   **Relevance**: An eigenvector of $P_\pi$ with eigenvalue 1.

**b. Projection onto General Subspaces**

*   **Setting**: Projecting $x \in \mathbb{R}^n$ onto an $M$-dimensional subspace $U \subseteq \mathbb{R}^n$ with an ordered basis $(b_1, \dots, b_M)$ [149, Figure 3.11].
*   **Procedure**:
    1.  **Find Coordinates $\lambda_1, \dots, \lambda_M$**: The projection $\pi_U(x) = \sum_{i=1}^M \lambda_i b_i$. The coefficients $\lambda = (B^\top B)^{-1} B^\top x$, where $B = [b_1, \dots, b_M]$. This is derived by minimizing the squared error $||x - B\lambda||^2$, leading to the **normal equation** $B^\top B \lambda = B^\top x$.
    2.  **Find Projection Point $\pi_U(x)$**: $\pi_U(x) = B \lambda = B(B^\top B)^{-1} B^\top x$.
    3.  **Find Projection Matrix $P_\pi$**: $P_\pi = B(B^\top B)^{-1} B^\top$.
*   **Projection Error**: The squared error $||x - \pi_U(x)||$ is also called **reconstruction error**.
*   **Simplification for ONB**: If the basis $(b_1, \dots, b_M)$ is orthonormal, then $B^\top B = I$, simplifying the projection matrix to $P_\pi = BB^\top$ and coordinates to $\lambda = B^\top x$.
*   **Applications**: Used to derive **PCA** (Chapter 10) and **linear regression** (Chapter 9).

**c. Gram-Schmidt Orthogonalization**

*   A method to **constructively transform any basis into an orthogonal/orthonormal basis**.
*   It iteratively removes the components of vectors that are parallel to previously orthogonalized vectors.

**d. Projection onto Affine Subspaces**

*   **Setting**: Projecting a vector $x$ onto an **affine subspace** $L = x_0 + U$, where $x_0$ is a support point and $U$ is a vector subspace [160, Figure 3.13(a)].
*   **Procedure**: Transform the problem to a projection onto a vector subspace. Subtract $x_0$ from $x$ and $L$ to get $x - x_0$ and $U$. Project $x - x_0$ onto $U$ to get $\pi_U(x - x_0)$. Then translate back by adding $x_0$.
*   **Projection Formula**: $\pi_L(x) = x_0 + \pi_U(x - x_0)$.
*   **Distance**: $d(x, L) = ||x - \pi_L(x)|| = d(x - x_0, U)$.
*   **Applications**: Used to derive the concept of a **separating hyperplane in SVM** (Section 12.1).

---

### **10. Rotations**

Rotations are linear mappings characterized by **preserving distances and angles**.

*   **Definition**: A **rotation** is an automorphism of a Euclidean vector space that rotates a plane by an angle $\theta$ about the origin. Positive angles typically denote counterclockwise rotation.
*   **Applications**: Computer graphics, robotics.

**a. Rotations in $\mathbb{R}^2$**

*   The **rotation matrix $R(\theta)$** transforms the standard basis vectors (and thus any vector) by angle $\theta$ [164, 165, Figure 3.16].
*   $R(\theta) = \begin{bmatrix} \cos \theta & -\sin \theta \\ \sin \theta & \cos \theta \end{bmatrix}$.

**b. Rotations in $\mathbb{R}^3$**

*   In $\mathbb{R}^3$, rotations occur about a one-dimensional axis. There are three standard planar rotations about the standard basis vectors:
    *   **About $e_1$-axis**: $R_1(\theta) = \begin{bmatrix} 1 & 0 & 0 \\ 0 & \cos \theta & -\sin \theta \\ 0 & \sin \theta & \cos \theta \end{bmatrix}$ (rotation in $e_2e_3$ plane).
    *   **About $e_2$-axis**: $R_2(\theta) = \begin{bmatrix} \cos \theta & 0 & \sin \theta \\ 0 & 1 & 0 \\ -\sin \theta & 0 & \cos \theta \end{bmatrix}$ (rotation in $e_1e_3$ plane).
    *   **About $e_3$-axis**: $R_3(\theta) = \begin{bmatrix} \cos \theta & -\sin \theta & 0 \\ \sin \theta & \cos \theta & 0 \\ 0 & 0 & 1 \end{bmatrix}$ (rotation in $e_1e_2$ plane) [168, Figure 3.17].

**c. Rotations in $n$ Dimensions**

*   **Givens Rotation**: Generalizes rotations by fixing $n-2$ dimensions and restricting rotation to a two-dimensional plane.
*   $R_{ij}(\theta)$ is an identity matrix with specific trigonometric entries at rows/columns $i, j$.

**d. Properties of Rotations**

*   **Preserve distances**: $||x - y|| = ||R_\theta(x) - R_\theta(y)||$.
*   **Preserve angles**: The angle between $R_\theta x$ and $R_\theta y$ equals the angle between $x$ and $y$.
*   **Generally not commutative in 3D or more**: The order of rotations matters. They are commutative only in 2D or if they rotate about the same point.

---

### **11. Further Reading and Connections**

*   **Kernel Methods**: Inner products are central to kernel methods, which allow linear algorithms to be expressed purely by inner product computations (the "kernel trick"). This enables "non-linearization" of algorithms like **kernel-PCA** (Schölkopf et al., 1997) and is explored further in **Chapter 12 (SVMs)**.
*   **Optimization**: Orthogonal projections are used to iteratively minimize residual errors in optimization.
*   **Machine Learning Applications**: Projections are key in **linear regression** (Chapter 9) to minimize residual errors and in **PCA** (Chapter 10) for dimensionality reduction.
*   **Orthonormal Bases**: Important in optimization and numerical algorithms for solving linear equation systems (e.g., Krylov subspace methods).