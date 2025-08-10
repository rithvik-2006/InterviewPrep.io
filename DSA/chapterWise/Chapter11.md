Here are detailed revision notes for Chapter 11 on Hash Tables, including pseudocode and insights from the provided sources:

### Chapter 11: Hash Tables

Chapter 11 of "Cormen Introduction to Algorithms.pdf" provides a comprehensive introduction to hash tables as an effective data structure for implementing **dynamic sets** that support **dictionary operations** such as **INSERT**, **SEARCH**, and **DELETE**. While the **worst-case time** for a SEARCH operation in a hash table can be **O(n)**, similar to a linked list, **in practice and under reasonable assumptions, the average time for hash-table operations is O(1)**.

A hash table generalizes the concept of an ordinary array. Instead of using the key directly as an array index, the **array index is computed from the key using a hash function**. Hash tables typically use an array size proportional to the number of keys actually stored, making them efficient when the number of actual keys is small relative to the total possible keys.

The "DataStructuresCourse.pdf" further emphasises the practical utility of hashmaps (dictionaries in Python, maps in Go) in application code, noting their **O(1) average time complexity for lookups, insertions, and deletions**. It states that iterating over all keys and values in a hashmap still takes **O(n) time**.

The chapter covers several key aspects of hash tables:

#### 1. Direct-Address Tables (Section 11.1)

Direct addressing is a simple technique used when the **universe of possible keys (U) is reasonably small** (e.g., from 0 to m-1). It assumes that no two elements have the same key.

*   **Representation**: A direct-address table, denoted `T[0...m-1]`, is an array where each position (slot) `k` directly corresponds to a key `k` in the universe `U`. If the set contains an element with key `k`, `T[k]` points to that element; otherwise, `T[k]` is `NIL`.
*   **Performance**: All dictionary operations are trivial to implement and take **O(1) time**.

**Pseudocode for Direct-Address Table Operations:**
```pseudocode
DIRECT-ADDRESS-SEARCH(T, k)
1 return T[k]

DIRECT-ADDRESS-INSERT(T, x)
1 T[x:key] = x

DIRECT-ADDRESS-DELETE(T, x)
1 T[x:key] = NIL
```

#### 2. Collision Resolution by Chaining (Section 11.2)

Collisions occur when more than one key maps to the same array index. Chaining is the simplest technique to resolve these collisions.

*   **Mechanism**: All elements that hash to the same slot are placed into the **same linked list**. Slot `j` in the hash table contains a pointer to the head of the list of all stored elements that hash to `j`; if no such elements exist, the slot contains `NIL`.
*   **Performance**: If the linked lists are doubly linked, all dictionary operations (INSERT, DELETE, SEARCH) can be supported in **O(1) time on average**.
    *   The "DataStructuresCourse.pdf" mentions that a naive hash function (e.g., summing Unicode values and taking modulo) can lead to collisions, especially with a small backing array, and that good hashmaps have strategies to handle these.

#### 3. Hash Functions (Section 11.3)

Hash functions are crucial for computing array indices from keys.

*   **Desired Properties**: A good hash function should ideally distribute keys uniformly across the hash table's slots. It must always return the same integer for the same key and always return a valid index within the array bounds.
*   **Division Method**: A common method where `h(k) = k mod m`, where `m` is the table size. Choosing `m` as a **prime number not too close to an exact power of 2** is often recommended for better distribution.
*   **Universal Hashing**: This is a powerful technique where the hash function `h` is chosen randomly from a carefully designed **universal class of hash functions**.
    *   **Benefit**: Using universal hashing and chaining in an initially empty table with `m` slots, it takes an **expected time of O(n)** to handle any sequence of `n` INSERT, SEARCH, and DELETE operations containing O(m) INSERT operations. This means the **expected time for each individual operation is O(1)**.

#### 4. Open Addressing (Section 11.4)

Open addressing is an alternative collision resolution method where **all elements occupy the hash table itself**; no elements are stored outside.

*   **Mechanism**: Each table entry contains either an element of the dynamic set or `NIL`. When searching, the algorithm systematically examines table slots until the desired element is found or it's determined that the element is not in the table.
*   **Advantage**: It avoids pointers, which can free up memory for more slots, potentially leading to fewer collisions and faster retrieval.
*   **Limitation**: The hash table can "fill up", meaning the **load factor (α) can never exceed 1**.
*   **Probe Sequence**: For every key `k`, the sequence `h(k, 0), h(k, 1), ..., h(k, m-1)` must be a permutation of `0, ..., m-1` to ensure every position is eventually considered.
*   **Common Probing Methods**:
    *   **Linear Probing**: `h(k, i) = (h'(k) + i) mod m`.
    *   **Quadratic Probing**: `h(k, i) = (h'(k) + c1*i + c2*i^2) mod m`.
    *   **Double Hashing**: `h(k, i) = (h1(k) + i*h2(k)) mod m`. This method typically performs very close to "ideal" uniform hashing.

*   **Pseudocode for Insertion (Conceptual, based on text description):**
    *(Note: The "Cormen" source describes the behaviour of HASH-INSERT but does not provide step-by-step pseudocode for it. This is a generic representation based on the description.)*
    ```pseudocode
    HASH-INSERT(T, k)
        for i = 0 to T.length - 1  // Iterate through potential probe sequence
            j = h(k, i)           // Calculate next probe position
            if T[j] == NIL or T[j] == DELETED  // Check if slot is empty or marked for deletion
                T[j] = k          // Store the key
                return j          // Return the slot number
        error "hash table overflow" // All slots examined, table is full
    ```

*   **Performance (assuming Uniform Hashing for analysis)**:
    *   **Unsuccessful Search**: Expected probes are at most **1/(1 - α)**.
    *   **Insertion**: Expected probes are at most **1/(1 - α)**.
    *   **Successful Search**: Expected probes are at most **(1/α) * ln(1/(1 - α))**. For example, if the table is 50% full (α=0.5), an unsuccessful search takes at most 2 probes, and a successful search takes less than 1.387 probes on average.

#### 5. Perfect Hashing (Section 11.5)

Perfect hashing provides **O(1) memory accesses in the worst case** for performing a search.

*   **Applicability**: It is used when the **set of keys is static**, meaning the keys never change once stored (e.g., reserved words in a programming language, file names on a CD-ROM).
*   **Mechanism**: It employs **two levels of hashing**, with universal hashing at each level.
    *   A **first-level hash function** maps keys to slots in a primary hash table.
    *   Any keys that collide (map to the same slot) are then re-hashed into a **secondary hash table**.
    *   Crucially, the secondary hash tables are constructed such that **no collisions occur within them**.
*   **Memory Usage**: If the first-level table size is `m = n` (where `n` is the number of keys), the **expected total memory** required for both the primary and all secondary hash tables is **O(n)**. This is achieved by setting the size of each secondary hash table `mj` to `n_j^2`, where `n_j` is the number of keys mapping to slot `j` in the first level.

#### Key Properties and Practical Considerations (from "DataStructuresCourse.pdf")

"DataStructuresCourse.pdf" highlights several practical aspects of hashmaps:

*   **Speed**: Hashmaps are considered one of the fastest data structures due to their **average O(1) time complexity** for basic operations.
*   **Key-Value Mapping**: They primarily map **hashable keys to any values**. The hashable nature of a key means the hash function can consistently convert it into an index.
*   **Unordered Nature**: Hashmaps are typically **unordered**; they do not maintain any specific order of keys. This means they are **not suitable for range queries** (e.g., finding the top 10 elements).
*   **Collision Resistance**: A "good" hashmap is **collision-resistant**, meaning it minimises the chance of different keys mapping to the same bucket and provides strategies to handle collisions when they occur (e.g., by ensuring sufficient space or employing secondary probing). A naive hash function (like simple sum of Unicode values) can easily lead to collisions.
*   **Efficient Resizing**: For optimal performance and memory usage, hashmaps should start with a small backing array and **resize efficiently** (growing larger as more elements are added) to avoid running out of room for new key-value pairs. This often involves a trade-off between memory and computational speed, where a bit more memory is used to maintain faster operations.
*   **Uniform Distribution**: The hash function should ensure a **uniform distribution** of keys across the table's slots to minimise collisions and optimise overall speed.