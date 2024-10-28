### 12. Fundamental Algorithms

#### 12.1 Sorting Algorithms

Sorting algorithms are essential for organizing data in a specific order, which can improve the efficiency of searching and data processing. Common sorting algorithms include:

1. **Bubble Sort**: A simple algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. Its average and worst-case time complexity is O(n²).

2. **Selection Sort**: This algorithm divides the list into a sorted and an unsorted part, repeatedly selecting the smallest (or largest) element from the unsorted part to add to the sorted part. Its time complexity is also O(n²).

3. **Insertion Sort**: Builds the sorted array one element at a time by repeatedly taking an element from the unsorted part and inserting it into the correct position. Its average time complexity is O(n²), but it performs well for small or nearly sorted datasets.

4. **Merge Sort**: A divide-and-conquer algorithm that divides the list into halves, recursively sorts them, and then merges the sorted halves. It has a time complexity of O(n log n).

5. **Quicksort**: Another divide-and-conquer algorithm that selects a 'pivot' and partitions the array around it, sorting the partitions recursively. Its average-case time complexity is O(n log n), but its worst-case is O(n²).

6. **Heapsort**: This algorithm builds a max heap from the data, then extracts the maximum element repeatedly to produce a sorted list. It has a time complexity of O(n log n).

#### 12.2 Search Algorithms

Search algorithms are used to find specific elements or sets of elements within a data structure. Key search algorithms include:

1. **Linear Search**: A straightforward method that checks each element in the list sequentially until the desired element is found. Its time complexity is O(n).

2. **Binary Search**: A much more efficient algorithm that works on sorted arrays by repeatedly dividing the search interval in half. It has a time complexity of O(log n).

3. **Depth-First Search (DFS)**: An algorithm for traversing or searching tree or graph data structures, going as deep as possible down one branch before backing up. Its time complexity is O(V + E), where V is vertices and E is edges.

4. **Breadth-First Search (BFS)**: This algorithm explores all neighbors at the present depth before moving on to nodes at the next depth level. It has the same time complexity as DFS, O(V + E).

#### 12.3 Graph Algorithms

Graph algorithms are crucial for solving problems related to networks, relationships, and connections. Key algorithms include:

1. **Dijkstra's Algorithm**: This algorithm finds the shortest path from a source vertex to all other vertices in a graph with non-negative weights. It has a time complexity of O(V²) or O(E log V) with a priority queue.

2. **A* Search Algorithm**: A heuristic-based search algorithm that finds the shortest path between nodes by using a cost function. It combines the benefits of DFS and BFS.

3. **Kruskal's and Prim's Algorithms**: Both are used to find the minimum spanning tree of a graph. Kruskal’s algorithm uses a greedy approach, while Prim’s algorithm grows the spanning tree one vertex at a time.

#### 12.4 Dynamic Programming

Dynamic programming is a method for solving complex problems by breaking them down into simpler subproblems and storing the results to avoid redundant computations. Common applications include:

1. **Fibonacci Sequence**: A classic example where dynamic programming can reduce the time complexity from O(2^n) to O(n) by storing previously computed values.

2. **Knapsack Problem**: A problem that asks how to maximize the value of items placed in a knapsack without exceeding its capacity.

3. **Longest Common Subsequence**: Finding the longest subsequence common to two sequences, with applications in bioinformatics and text comparison.

---

**Timestamp**: 2024-10-28 14:15:00  
**Summary**: Overview of fundamental algorithms including sorting, searching, graph algorithms, and dynamic programming, highlighting key techniques and time complexities.  
**Lines**: 64  
**Characters**: 1402  
```bash
nvim fundamental_algorithms_rust.md
```
