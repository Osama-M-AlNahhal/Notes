# Sliding Window

**Ways to identify when to use the sliding window pattern :**
1. The problem input is a linear data structure such as a linked list, array, or string.
2. You’re asked to find the longest/shortest substring, subarray, or a desired value.

**Problems :**
-   Maximum sum subarray of size ‘K’ (easy)
-   Longest substring with ‘K’ distinct characters (medium)
-   String anagrams (hard)


---

# Two Pointers or Iterators

**Ways to identify when to use the Two Pointer pattern :**
1. It will feature problems where you deal with sorted arrays (or Linked Lists) and need to find a set of elements that fulfill certain constraints.
2. The set of elements in the array is a pair, a triplet, or even a subarray

**Porblems :**
-   Squaring a sorted array (easy)
-   Triplets that sum to zero (medium)
-   Comparing strings that contain backspaces (medium)

---

# Fast and Slow pointers

**Ways to identify when to use the Fast and Slow pointers pattern :**
1. The problem will deal with a loop in a linked list or array.
2. When you need to know the position of a certain element or the overall length of the linked list.

- **Don't use this in a singly linked list where you can’t move in a backwards direction, instead use [[The 14 Patterns#Two Pointers or Iterators||Two Pointers]]

**Problems :**
-   Linked List Cycle (easy)
-   Palindrome Linked List (medium)
-   Cycle in a Circular Array (hard)

---

# Merge Intervals

**There are 6 different ways for two intervals to relate to eachother :**
1. a and b do not overlap.
2. a and b overlap (b ends after a).
3. a and b overlap (a ends after b).
4. a completely overlaps b.
5. b completely overlaps a.

**Ways to identify when to use the Merge Intervals pattern :**
1. If you’re asked to produce a list with only mutually exclusive intervals.
2. If you hear the term “overlapping intervals”.

**Problems :**
-   Intervals Intersection (medium)
-   Maximum CPU Load (hard)

---

# Cyclic sort

**Ways to identify when to use the Cyclic sort pattern :**
1. They will be problems involving a sorted array with numbers in a given range
2. If the problem asks you to find the missing/duplicate/smallest number in an sorted/rotated array

**Porblems :**
-   Find the Missing Number (easy)
-   Find the Smallest Missing Positive Number (medium)


---

# In-place reversal of linked list

**Ways to identify when to use the In-place reversal of linked list pattern :**
1. If you’re asked to reverse a linked list without using extra memory.


**Problem :**
-   Reverse a Sub-list (medium)
-   Reverse every K-element Sub-list (medium)

---

# Tree BFS

**Ways to identify when to use the Tree BFS pattern :**
-   If you’re asked to traverse a tree in a level-by-level fashion (or level order traversal)


**Problems :
-   Binary Tree Level Order Traversal (easy)
-   Zigzag Traversal (medium)


---

# Tree DFS
*using recursion (or a stack for the iterative approach)*

**Ways to identify when to use the Tree DFS pattern :**
1. If you’re asked to traverse a tree with in-order, preorder, or postorder DFS.
2. If the problem requires searching for something where the node is closer to a leaf.

**Problems :**
-   Sum of Path Numbers (medium)
-   All Paths for a Sum (medium)


---

# Two heaps

**Ways to identify when to use the Two heaps pattern :**
1. Useful in situations like Priority Queue, Scheduling
2. If the problem states that you need to find the smallest/largest/median elements of a set
3. Sometimes, useful in problems featuring a binary tree data structure.

**Problems :**
-   Find the Median of a Number Stream (medium)

---

# Subsets

**How it works :**

> 	Given a set of \[1, 5, 3]
> 		1.  Start with an empty set: [[]]
> 		2. Add the first number (1) to all the existing subsets to create new subsets: [[], [1]]
> 		3. Add the second number (5) to all the existing subsets: [[], [1], [5], [1,5]]
> 		4. Add the third number (3) to all the existing subsets: [[], [1], [5], [1,5], [3], [1,3], [5,3], [1,5,3]]


**Ways to identify when to use the subsets pattern :**
-   Problems where you need to find the combinations or permutations of a given set


**Problems :**
-   Subsets With Duplicates (easy)
-   String Permutations by changing case (medium)


---

# Modified Binary Search

**Problems :**
- Order-agnostic Binary Search (easy)
- Search in a Sorted Infinite Array (medium)

---

# Top K elements
*best data structure for this is the heap*

**Ways to identify when to use the Top K elements pattern :**
1. If you’re asked to find the top/smallest/frequent ‘K’ elements of a given set.
2. If you’re asked to sort an array to find an exact element.

**Problems :**
-   Top ‘K’ Numbers (easy)
-   Top ‘K’ Frequent Numbers (medium)

---

# K-way Merge
*solve problems that involve a set of sorted arrays*

**How it works :**

> 	Given a set of \[1, 5, 3]
> 		1.  Insert the first element of each array in a Min Heap.
> 		2.  After this, take out the smallest (top) element from the heap and add it to the merged list.
> 		3.  After removing the smallest element from the heap, insert the next element of the same list into the heap.
> 		4.  Repeat steps 2 and 3 to populate the merged list in sorted order.


**Ways to identify when to use the K-way Merge pattern :**
-   The problem will feature sorted arrays, lists, or a matrix
-   If the problem asks you to merge sorted lists, find the smallest element in a sorted list.

**Problems :**
-   Merge K Sorted Lists (medium)
-   K Pairs with Largest Sums (Hard)

---

# Topological sort
*huhhhhhhhhhhhhhhhhhhhh??????*

