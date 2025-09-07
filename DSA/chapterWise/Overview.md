## Chapter 1: Algorithms Intro

An **algorithm** is a specific set of unambiguous, implementable instructions for solving a problem with a finite number of steps. In computer science, they are often described using **pseudocode**, a high-level, plain-English description independent of a specific programming language. Learning Data Structures and Algorithms (DSA) is crucial for developers to understand the **performance implications** of their code and to develop problem-solving skills. The key is to understand how algorithms work, not just to memorize them.

### Examples of Simple Algorithms
* **Find Minimum:** An algorithm to find the smallest number in a list by iterating through it and updating a `min` variable. It handles the edge case of an empty list by returning `None`.
* **Sum Function:** Calculates the total sum of a list of numbers. An edge case for an empty list is to return 0.
* **Reverse String:** Loops through a string from last to first, adding characters to a new string.

***
## Chapter 2: Math

A basic understanding of mathematics is essential for analyzing algorithms.

* **Exponents:** Indicate how many times a number is multiplied by itself (e.g., $5^3 = 5 \times 5 \times 5$). In Python, `**` is the exponentiation operator. Exponential growth is very fast.
* **Geometric Sequence:** A sequence where each number is found by multiplying the previous one by a fixed number (**R**). The formula is $A_n = A_1 \times R^{(n-1)}$.
* **Nonlinear Growth:** Exponential growth (e.g., $x^2$) is significantly faster than linear growth (e.g., $2x$). It's generally a performance issue in code unless used intentionally, such as in cryptography.
* **Logarithms:** The inverse of exponentiation. $\log_B X = Y$ means $B^Y = X$. Base 2 logarithms are common in computing because of its binary nature. Logarithmic growth is very slow, making algorithms with this complexity very fast. An example is a `get_influencer_score` function, where the score is calculated using `engagement_percentage * log2(follower_account)`.
* **Factorials:** The product of all positive integers up to a given number **n** (e.g., $5! = 5 \times 4 \times 3 \times 2 \times 1 = 120$). Factorial growth ($O(N!)$) is even faster than exponential growth ($O(2^N)$), making such algorithms impractical for all but the smallest inputs.

---
## Chapter 3: Big-O Analysis

**Big O notation** is a method for classifying algorithms based on how their **worst-case runtime** scales with the size of the input. It focuses on the proportional change, ignoring constant factors.

* **O(1) - Constant Time:** The fastest category. Runtime is constant regardless of input size. Examples include retrieving the length of a list or a value from a dictionary by its key.
* **O(log N) - Logarithmic Time:** Runtime grows very slowly. The problem size is typically halved at each step. An example is **Binary Search**, which is extremely efficient.
* **O(N) - Linear Time:** Runtime is directly proportional to the input size. Examples include a single loop that iterates over a list, like `find_minimum`.
* **O(N log N) - Linearithmic Time:** Faster than quadratic but slower than linear. This is the complexity of efficient sorting algorithms like **Merge Sort** and **Quick Sort**.
* **O(N^2) - Quadratic Time:** Runtime grows parabolically. This often occurs with **nested loops** where each loop iterates over the input size.
* **O(2^N) - Exponential Time:** Runtime grows so quickly it's impractical. Only useful in niche cases like cryptography, where the goal is to make computation difficult.
* **O(N!) - Factorial Time:** Runtime grows faster than exponential and is essentially unusable. An example is an algorithm that generates all possible permutations of a list.

---
## Chapter 4: Sorting Algorithms

Sorting algorithms arrange items in a specific order. While most languages have built-in sorting functions, understanding their inner workings is fundamental.

* **Bubble Sort:**
    * **Description:** Repeatedly steps through the list, comparing and swapping adjacent elements until the list is sorted.
    * **Complexity:** Worst-case is **O(N^2)**. Best-case is **O(N)** for already sorted data.
    * **Value:** A simple concept for learning purposes, but highly inefficient.
* **Merge Sort:**
    * **Description:** A recursive "divide and conquer" algorithm that splits the list into halves, sorts them, and then merges the sorted halves back together.
    * **Complexity:** **O(N log N)** for all cases.
    * **Pros:** Very efficient and a **stable sort** (maintains relative order of equal elements).
    * **Cons:** Requires **extra memory** for sublists.
* **Insertion Sort:**
    * **Description:** Builds a sorted list one item at a time by inserting each element into its correct position within the sorted part of the list.
    * **Complexity:** Average/worst-case is **O(N^2)**. Best-case is **O(N)** for already sorted data.
    * **Use Case:** Efficient for **very small datasets** or lists that are **mostly sorted**.
* **Quick Sort:**
    * **Description:** A recursive "divide and conquer" algorithm that chooses a **pivot** element, partitions the array around it, and then recursively sorts the sub-arrays. It sorts the list in-place.
    * **Complexity:** Average case is **O(N log N)**. Worst case is **O(N^2)**, which can be avoided by choosing the pivot wisely (e.g., shuffling the input).
    * **Pros:** Fast and memory efficient in the average case.

---
## Chapter 5: Exponential Time

Algorithms are categorized as either polynomial time or exponential time.

* **Polynomial Time (P):** Algorithms that run in $O(N^k)$ time for any constant k. These are considered **practical to solve**.
* **Exponential Time:** Algorithms that grow at an exponential rate, like $O(2^N)$ or $O(N!)$. These are generally **too slow to be practical**. An example is the recursive solution to the Fibonacci sequence, which can be made polynomial time by using an iterative loop and storing previous values (a form of dynamic programming).
* **Power Set:** An example of an exponential time problem is generating the power set (all possible subsets) of a set, as the number of subsets grows exponentially.

---
## Chapter 6: Data Structures Intro

A **data structure** is a format for organizing and storing data to enable efficient access and modification. They rely on algorithms for their operations.

* **Key Characteristics:** Store and organize data, contain algorithmic functions, and reside in memory.
* **Python's Built-in Structures:**
    * **Lists:** Ordered collections with operations like appending (O(1) on average), indexing (O(1)), and searching (O(N)). Deleting from the middle is slow, at O(N).
    * **Dictionaries:** Key-value mappings (Hashmaps).
    * **Tuples:** Immutable lists.

---
## Chapter 7: Stacks

A stack is a data structure following the **Last In, First Out (LIFO)** principle. Items are only added or removed from the **top**.

* **Operations:**
    * **Push:** Adds an item to the top.
    * **Pop:** Removes and returns the top item.
    * **Peek:** Returns the top item without removing it.
* **Big O Complexity:** All operations are **O(1)**.
* **Use Cases:** Undo/redo functionality, browser history (the "back" button), and function call management.

---
## Chapter 8: Queues

A queue is a data structure following the **First In, First Out (FIFO)** principle. Items are added to the **tail** and removed from the **head**.

* **Operations:**
    * **Enqueue:** Adds an item to the tail.
    * **Dequeue:** Removes and returns the item from the head.
* **Big O Complexity:** All operations are **O(1)** if implemented efficiently (e.g., using a linked list). Using a Python list's `insert(0, item)` for `enqueue` would result in a slow O(N) operation.
* **Use Cases:** Modeling waiting lines, task scheduling, or ordered backlogs.

---
## Chapter 9: Linked Lists

A **linked list** is an ordered collection of **nodes** where each node contains a value and a pointer (`next`) to the next node. Nodes are not stored contiguously in memory. 

* **Advantages:** **O(1)** for insertion or deletion at the beginning or middle, as it only requires updating a few pointers.
* **Disadvantages:**
    * No random access, so finding an item by index is **O(N)**.
    * Slower traversal in practice due to non-contiguous memory access.
    * Higher memory overhead due to storing pointers.
* **Doubly Linked List:** Each node has a `previous` pointer in addition to the `next` pointer, allowing for traversal in both directions.

---
## Chapter 10: Binary Trees

A **binary tree** is a hierarchical data structure where each node has at most two children: a `left` child and a `right` child.

* **Binary Search Tree (BST):** A type of binary tree where for any given node, all values in its **left subtree** are less than its value, and all values in its **right subtree** are greater. This property enables very efficient operations.
* **Fast Operations:** Searching, inserting, updating, and deleting nodes are all **O(log N)** on average, as the search space is halved at each step.
* **Tree Traversals (all O(N)):**
    * **In-order Traversal:** Visits the left subtree, then the root, then the right subtree. This retrieves the nodes in **sorted order**.
    * **Pre-order Traversal:** Root -> Left -> Right.
    * **Post-order Traversal:** Left -> Right -> Root.

---
## Chapter 11: Red Black Trees

A **Red Black Tree** (RBT) is a **self-balancing Binary Search Tree**. This is a critical distinction because a standard BST can become unbalanced (degrading to O(N) performance) if items are inserted in a sorted order.

* **Mechanism:** Each node is assigned a color (**red** or **black**). The tree follows a strict set of rules about these colors to maintain balance.
* **Rotations:** When a node is inserted or deleted, the RBT performs **rotations** to "fix" the tree's balance, ensuring its height remains logarithmic.
* **Complexity:** All operations (insert, delete, lookup) are guaranteed to be **O(log N)**, even in the worst case.

---
## Chapter 12: Hashmaps

A **hashmap** (or dictionary) is a data structure for storing and retrieving key-value pairs very efficiently. Python's `dict` is a hashmap.

* **Complexity:** Lookups, insertions, and deletions are typically **O(1) on average**.
* **Underlying Implementation:** Hashmaps are usually built on top of an array.
* **Hash Function:** A function that takes a key as input and converts it into a valid **integer index** for the backing array. It must produce the same index for the same key. A robust hashmap implementation must also handle **collisions** (when different keys hash to the same index).

---
## Chapter 13: Tries

A **trie** (pronounced "try") is a tree-like data structure highly optimized for **text processing and prefix matching**.

* **Structure:** Words are stored character by character. Each node represents a character, and the entire structure is often implemented with nested dictionaries. A special marker indicates the end of a word.
* **Advantages:**
    * Highly efficient for **prefix matching** (e.g., autocompletion).
    * Can be memory-efficient by reusing common prefixes.
* **Complexity:** `add` and `exists` operations are **O(M)**, where M is the length of the word. For typical words, this is practically constant time.

---
## Chapter 14: Graphs

A **graph** is a flexible data structure representing relationships between entities, consisting of **vertices (nodes)** and **edges (connections)**. Unlike a tree, a node can have multiple parents.

* **Modeling Graphs:**
    * **Adjacency Matrix:** A 2D array where `matrix[U][V] = True` indicates an edge between vertices U and V. Space-inefficient for graphs with few edges (**sparse graphs**).
    * **Adjacency List:** A dictionary where each key is a vertex and the value is a list (or set) of its neighbors. More space-efficient for sparse graphs. 

---
## Chapter 15: BFS and DFS

**Graph traversal** algorithms systematically visit all the nodes in a graph.

* **Breadth-First Search (BFS):**
    * **Strategy:** Explores the graph **level by level**, using a **queue** to manage the order of vertices to visit. It goes "wide" before it goes "deep."
    * **Complexity:** **O(V + E)**.
    * **Use Cases:** Finding the **shortest path** in an unweighted graph, web crawling.
* **Depth-First Search (DFS):**
    * **Strategy:** Explores as **deep as possible** along each branch before backtracking. It's typically implemented **recursively** (which uses the call stack).
    * **Use Cases:** Good for problems with a deep solution, or for when memory is a concern with a wide graph.

---
## Chapter 16: P vs NP

P vs. NP is an unsolved problem in computer science concerning the efficiency of solving and verifying computational problems.

* **P (Polynomial Time):** The class of problems that can be **solved** quickly (in polynomial time).
* **NP (Non-deterministic Polynomial Time):** The class of problems whose solutions can be **verified** quickly (in polynomial time). **P is a subset of NP**.
* **P vs NP Question:** Does P = NP? In other words, if a problem's solution can be quickly verified, can it also be quickly found? Most computer scientists believe **P ≠ NP**.
* **Traveling Salesman Problem (TSP):** A classic example of a problem in **NP**. While verifying a given solution (a path) is fast (O(N)), finding the optimal solution by checking all permutations is extremely slow (O(N!)).
* **NP-Complete (NPC):** Problems that are both in NP and are the "hardest" problems in NP. If a fast algorithm were found for any NPC problem, it could be applied to all other problems in NP.
* **NP-Hard:** A class of problems that are at least as hard as the hardest problems in NP. An NP-Hard problem does not necessarily have to be in NP itself.