Chapter 7 in the provided sources covers two distinct topics: **Quicksort** from "Cormen Introduction to Algorithms.pdf" and **Stacks** from "DataStructuresCourse.pdf". Below are detailed revision notes for both, including pseudocode.

---

### 1. Quicksort (from "Cormen Introduction to Algorithms.pdf" Chapter 7)

**Quicksort** is an efficient, **in-place sorting algorithm**, meaning it sorts an array without requiring significant additional memory beyond a constant amount.

*   **Algorithm Overview**
    *   Quicksort's average-case running time is **O(n lg n)**.
    *   However, in its worst case, its running time can degrade to **O(n^2)**. This occurs if the input array is already sorted (either in increasing or decreasing order), leading to unbalanced partitions.
    *   It operates on the **divide-and-conquer** paradigm. The algorithm works by partitioning an array around a "pivot" element and then recursively sorting the sub-arrays on either side of the pivot.
    *   Compared to merge sort, quicksort is also O(n lg n) on average but is "lighter on memory usage". Insertion sort, while O(n^2) on average, can be faster than quicksort on *small* and *mostly sorted* lists due to smaller constant factors.

*   **Key Procedures**

    1.  **`PARTITION` Procedure**
        *   **Purpose**: This procedure rearranges a sub-array `A[p...r]` in-place around a chosen **pivot element**.
        *   **Mechanism**: After `PARTITION` executes, all elements **less than or equal to the pivot** are to its left, and all elements **greater than the pivot** are to its right. The pivot is then placed in its final sorted position between these two sections.
        *   **Pivot Selection**: The version described in the source arbitrarily chooses the **last element** of the sub-array `A[r]` as the pivot.
        *   **Running Time**: `PARTITION` has a running time of **O(n)**, where `n` is the size of the sub-array being partitioned.
        *   **Pseudocode (Lomuto Partition Scheme)**:
            ```pseudocode
            PROCEDURE PARTITION(A, p, r)
                x = A[r] // Select the last element as the pivot
                i = p - 1 // Initialize a pointer 'i' to track the boundary of smaller elements
                FOR j = p TO r - 1 DO // Iterate through the sub-array from 'p' to 'r-1'
                    IF A[j] <= x THEN // If current element is less than or equal to the pivot
                        i = i + 1 // Increment 'i'
                        EXCHANGE A[i] WITH A[j] // Swap A[i] and A[j] to place smaller element to the left
                    END IF
                END FOR
                EXCHANGE A[i + 1] WITH A[r] // Place the pivot (original A[r]) into its final sorted position
                RETURN i + 1 // Return the pivot's final index
            END PROCEDURE
            ```

    2.  **`QUICKSORT` Procedure**
        *   **Purpose**: To sort an entire array (or sub-array) by repeatedly partitioning it.
        *   **Mechanism**:
            1.  If the sub-array has more than one element (`p < r`), it calls `PARTITION` to rearrange the elements around a pivot, obtaining the pivot's final index `q`.
            2.  It then **recursively calls itself** on the sub-array to the left of the pivot (`A[p...q-1]`).
            3.  And recursively calls itself on the sub-array to the right of the pivot (`A[q+1...r]`).
        *   **Pseudocode**:
            ```pseudocode
            PROCEDURE QUICKSORT(A, p, r)
                IF p < r THEN // Base case: If the sub-array has at least two elements
                    q = PARTITION(A, p, r) // Partition the array and get the pivot's final index
                    QUICKSORT(A, p, q - 1) // Recursively sort the left sub-array
                    QUICKSORT(A, q + 1, r) // Recursively sort the right sub-array
                END IF
            END PROCEDURE
            ```

*   **Performance Considerations**
    *   **Worst-case Complexity (O(n^2))**: Occurs when partitioning is consistently unbalanced, such as when the input array is already sorted (either increasing or decreasing). In this scenario, the `PARTITION` function might be called `n` times, once for every element in the input.
    *   **Best-case / Average-case Complexity (O(n lg n))**: Achieved when partitioning consistently produces balanced sub-problems (e.g., the pivot is always the middle element). This results in `log n` calls to `PARTITION`.
    *   **Fixing Quicksort**: To mitigate the worst-case performance, variations are used:
        *   **Randomized Quicksort**: Shuffling the input array randomly before sorting can effectively prevent the worst-case scenario, making the O(n lg n) performance highly probable.
        *   **Median-of-Three Approach**: Choosing the median of three elements (e.g., first, middle, and last) as the pivot for each partition can improve the balance of splits.

---

### 2. Stacks (from "DataStructuresCourse.pdf" Chapter 7)

**Stacks** are fundamental data structures designed for managing ordered collections of items. Their defining characteristic is that they follow the **LIFO (Last In, First Out)** principle.

*   **Definition and Characteristics**
    *   Items can only be **added to (pushed)** or **removed from (popped)** the **top** of the stack.
    *   Analogy: Imagine a **stack of plates** – new plates are added on top, and plates are only taken from the top. To access an item at the bottom, all items above it must first be removed.
    *   Despite their restrictive nature, stacks are **extremely fast**, with all core operations typically completing in **O(1)** time.

*   **Common Operations and Pseudocode**
    Stacks are often implemented on top of simpler, built-in data structures like lists or arrays. The following pseudocode assumes an underlying list named `items`.

    1.  **`PUSH(item)`**: Adds an `item` to the top of the stack.
        ```pseudocode
        PROCEDURE PUSH(stack, item)
            stack.items.append(item) // Add item to the end of the underlying list, which represents the top of the stack
        END PROCEDURE
        ```

    2.  **`POP()`**: Removes and returns the item currently at the top of the stack.
        ```pseudocode
        PROCEDURE POP(stack)
            IF LENGTH(stack.items) == 0 THEN // Check if the stack is empty (underflow condition)
                RETURN NONE // Return a special value (e.g., None) or raise an error
            ELSE
                val = stack.items[LENGTH(stack.items) - 1] // Get the last item (top of the stack)
                REMOVE stack.items[LENGTH(stack.items) - 1] // Remove the item from the list
                RETURN val
            END IF
        END PROCEDURE
        ```

    3.  **`PEEK()`**: Returns the item at the top of the stack without removing it.
        ```pseudocode
        PROCEDURE PEEK(stack)
            IF LENGTH(stack.items) == 0 THEN // Check if the stack is empty
                RETURN NONE
            ELSE
                RETURN stack.items[LENGTH(stack.items) - 1] // Return the last item (top of the stack)
            END IF
        END PROCEDURE
        ```

    4.  **`SIZE()`**: Returns the number of items currently in the stack.
        ```pseudocode
        PROCEDURE SIZE(stack)
            RETURN LENGTH(stack.items) // Return the number of elements in the underlying list
        END PROCEDURE
        ```

*   **Performance and Use Cases**
    *   **Big-O Complexity**: All four core operations (`PUSH`, `POP`, `PEEK`, `SIZE`) have a time complexity of **O(1)**. This means their execution time remains constant regardless of the number of items in the stack.
    *   **Accessing Bottom Item**: If you need to retrieve an item from the *bottom* of a stack using only standard stack operations, it would take **O(n) time**, as you would need to `POP` every item above it first.
    *   **Real-world Applications**: Stacks are commonly used for:
        *   **Undo/Redo functionality** in applications (e.g., text editors, image editing software).
        *   **Browser navigation history** (e.g., the back button).
        *   **Function call management** (the "call stack" in programming languages).
        *   **Expression evaluation** (e.g., parsing mathematical expressions).
        *   **Checking balanced parentheses** in strings or code.