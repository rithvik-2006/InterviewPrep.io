Chapter 8 of the provided source, "Cormen Introduction to Algorithms.pdf", is titled **"Sorting in Linear Time"**. This chapter focuses on sorting algorithms that can achieve a time complexity better than the theoretical lower bound for comparison sorts.

It is important to note that the other provided source, "DataStructuresCourse.pdf", does not contain specific information regarding a "Chapter 8" that aligns with "Sorting in Linear Time" or covers the specific algorithms discussed in Cormen's Chapter 8, such as Counting Sort and Radix Sort. While "DataStructuresCourse.pdf" does discuss sorting algorithms like Merge Sort, Insertion Sort, and Quicksort, these are typically covered in earlier chapters or different contexts than linear-time sorting.

Here are the detailed revision notes for Chapter 8 from "Cormen Introduction to Algorithms.pdf":

### 1. Comparison Sort Lower Bounds

*   **Definition**: **Comparison sorts** are algorithms that determine the sorted order of an input array solely by comparing elements. Examples include Insertion Sort, Merge Sort, Heapsort, and Quicksort.
*   **Decision-Tree Model**: This model is used to analyse the performance limitations of comparison sorts.
*   **Lower Bound**: For any comparison sort, a **lower bound of Θ(n lg n)** on the worst-case running time for `n` inputs has been proven.
*   **Optimality**: This lower bound indicates that algorithms like Heapsort and Merge Sort, which have an O(n lg n) worst-case running time, are **asymptotically optimal comparison sorts**.
*   **Beyond Comparison Sorts**: Despite this lower bound, Chapter 8 demonstrates that it is possible to **"beat" this Θ(n lg n) lower bound** by employing sorting methods that are *not* based on comparisons. These are the linear-time sorting algorithms.

### 2. Counting Sort

**Counting Sort** is a stable sorting algorithm that operates in linear time under certain conditions.

*   **Principle**: It works by determining, for each input element `x`, the number of elements less than or equal to `x`. This information can then be used to directly place `x` into its correct sorted position in an output array.
*   **Time Complexity**: It runs in **O(n + k)** time, where `n` is the number of elements in the input array and `k` is the range of the input integers (i.e., the integers are in the range 0 to `k`).
*   **Limitations**: Counting Sort is efficient only when `k` is not significantly larger than `n`, typically when `k = O(n)`. If `k` is much larger, the `O(k)` term in the running time becomes dominant, making it less efficient than comparison sorts.
*   **Stability**: Counting Sort is inherently **stable**. Stability means that if two elements have the same value, their relative order in the input array is preserved in the output array. This property is crucial for algorithms like Radix Sort that use Counting Sort as a subroutine.

*   **Pseudocode (based on typical implementation and hints from)**:
    ```pseudocode
    PROCEDURE COUNTING-SORT(A, B, k)
        // A: Input array, A[1...n]
        // B: Output array, B[1...n]
        // k: Maximum value in A (elements are in range 0 to k)

        let C[0...k] be a new array

        // Initialize count array C with zeros
        FOR i = 0 TO k DO
            C[i] = 0
        END FOR

        // Store count of each element in C
        // C[i] now contains the number of elements equal to i
        FOR j = 1 TO A.length DO
            C[A[j]] = C[A[j]] + 1
        END FOR

        // Modify C so that C[i] now contains the number of elements
        // less than or equal to i (cumulative count)
        FOR i = 1 TO k DO
            C[i] = C[i] + C[i-1]
        END FOR

        // Place elements into their correct sorted position in output array B
        // Iterate downwards from A.length to 1 to ensure stability
        FOR j = A.length DOWNTO 1 DO
            B[C[A[j]]] = A[j]
            C[A[j]] = C[A[j]] - 1
        END FOR
    END PROCEDURE
    ```

### 3. Radix Sort

**Radix Sort** is a linear-time sorting algorithm for numbers with multiple digits.

*   **Principle**: It sorts numbers by processing individual digits (or characters). It works by applying a **stable sorting algorithm** to each digit, starting from the **least significant digit (LSD)** and moving towards the most significant digit (MSD).
*   **Requirement for Stability**: The correctness of Radix Sort critically depends on the intermediate sorting algorithm being **stable**. If a stable sort is not used, elements with the same value in a particular digit position might swap their relative order, which would break the correct sorted order established by previous passes on less significant digits.
*   **Time Complexity**: If `n` numbers each have `d` digits, and each digit can take on `k` possible values, then Radix Sort runs in **O(d * (n + k))** time when Counting Sort is used as the stable intermediate sort for each digit.
    *   For example, if numbers are represented in base `b` (meaning `k=b`), and there are `d` digits, the runtime is `O(d * (n + b))`.
*   **Applications**: Radix Sort is efficient for sorting integers, strings, or other data that can be parsed into fixed-size "digits".

*   **Pseudocode (Conceptual, highlighting stable sort dependency)**:
    ```pseudocode
    PROCEDURE RADIX-SORT(A, d)
        // A: Input array of numbers
        // d: Number of digits (or passes) for the numbers in A

        FOR i = 1 TO d DO // Iterate from the least significant digit (LSD) to the most significant digit (MSD)
            // Sort the array A using a stable sorting algorithm (e.g., COUNTING-SORT)
            // based on the value of the i-th digit (from right to left)
            A = STABLE-SORT(A, on_digit=i)
        END FOR
    END PROCEDURE
    ```

Chapter 8, therefore, introduces non-comparison-based sorting techniques that bypass the O(n lg n) lower bound, offering more efficient solutions for specific data types and distributions.