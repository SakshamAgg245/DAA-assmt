## SECTION A – Short Theory

**1. DP Essentials**  
Dynamic Programming involves three fundamental components:  
- **Optimal Substructure:** The overall optimal solution can be obtained by combining the optimal solutions of its subproblems.  
- **Overlapping Subproblems:** The same smaller problems appear repeatedly during computation and can be reused to save time.  
- **Memoization/Tabulation:** Results of subproblems are stored (in a table or cache) to avoid redundant recalculations, improving efficiency and reducing time complexity.

---

**2. DP vs Divide and Conquer**  
- **Overlap:** Dynamic Programming solves problems with overlapping subproblems, while Divide and Conquer handles independent subproblems that do not overlap.  
- **Reuse:** DP stores intermediate results for reuse, whereas D&C recomputes subproblems every time.  
**Examples:**  
- DP → Fibonacci numbers, shortest paths.  
- D&C → Merge Sort, Quick Sort.

---

**3. Principle of Optimality**  
A problem satisfies the **Principle of Optimality** if an optimal solution can be formed from the optimal solutions of its subproblems without re-evaluation of earlier decisions.  
**Example:** The Shortest Path problem (e.g., Dijkstra’s or Bellman-Ford) satisfies this principle as every subpath of an optimal path is itself optimal.

---

**4. Memoization**  
**Memoization:** It is a top-down dynamic programming approach where recursive results are stored once computed and reused when the same subproblem appears again.  
**Tabulation:** A bottom-up approach that iteratively builds the solution using a table, avoiding recursion and computing from smaller to larger subproblems.

---

**5. Branch and Bound Idea**  
Branch and Bound systematically explores the search space using a decision tree. Each branch represents a decision, and a **bound function** estimates the best possible solution from that branch.  
Bounding helps in **pruning** branches that cannot produce better solutions, effectively reducing the number of computations and improving efficiency.

---

## SECTION B – Algorithms & Recurrences

**6. Matrix Chain Multiplication**  
Given matrices A₁(5×4), A₂(4×6), A₃(6×2), A₄(2×7), we want the minimum number of scalar multiplications.

**Recurrence:**  
```
m[i, j] = 0, if i = j  
m[i, j] = min_{k=i to j-1} (m[i, k] + m[k+1, j] + p_{i-1} * p_k * p_j)
```
Here, `p` represents matrix dimensions.  
**Base Case:** A single matrix needs zero multiplications.  
**Minimum scalar multiplications:** 158

---

**7. Longest Common Subsequence (X = "ABCDGH", Y = "AEDFHR")**  

**Recurrence:**  
```
LCS(i, j) = 0, if i = 0 or j = 0  
LCS(i, j) = 1 + LCS(i-1, j-1), if X[i] = Y[j]  
LCS(i, j) = max(LCS(i-1, j), LCS(i, j-1)), otherwise
```
This formula finds the longest subsequence common to both strings without changing their order.  
**Base Case:** If either string is empty, LCS = 0.  
**LCS length:** 3 (common subsequence “ADH”).

---

**8. Optimal Binary Search Tree**  
Keys: {10, 20, 30}, probabilities p = {0.4, 0.3, 0.3}, q = 0.  
The goal is to minimize the expected search cost.

**Formulations:**  
```
w[i, j] = w[i, j-1] + p[j]  
e[i, j] = min_{r=i to j} (e[i, r-1] + e[r+1, j] + w[i, j])
```
**Base Case:**  
e[i, i-1] = 0, w[i, i-1] = 0  
**Minimum expected search cost:** 1.7 (root at key 10 or 20 yields optimal arrangement).

---

**9. 0/1 Knapsack – Branch & Bound**  
Given: W = 5; weights = {2, 3, 4, 5}; profits = {3, 4, 5, 6}.  
The objective is to maximize profit without exceeding capacity.

**Fractional Upper Bound Formula:**  
```
UB = current_profit + (remaining_capacity * next_item_profit / next_item_weight)
```
This upper bound helps in pruning non-promising nodes.  

**Nodes:**  
Level 0 (root) → (v=0, w=0, ub=10.5)  
Level 1 include item1 → (v=3, w=2, ub=9.33)  
Level 1 exclude item1 → (v=0, w=0, ub=9.0)  
The branch with higher bound is explored further.

---

**10. Travelling Salesman Problem – Dynamic Programming (Held–Karp)**  

**Recurrence:**  
```
C[S, j] = min_{k ∈ S, k ≠ j} [C[S - {j}, k] + D[k][j]]
Final answer = min_{j ≠ 1} [C[{2,3,4}, j] + D[j][1]]
```
Here, S represents the set of visited cities and D is the distance matrix.  
**Base Initialization:**  
C[{2},2] = D[1][2]  
C[{3},3] = D[1][3]  
C[{4},4] = D[1][4]  
This DP approach computes all subsets to find the minimum Hamiltonian cycle cost.
