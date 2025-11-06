# Unit3_Assignment_<YourName>

## SECTION A – Short Theory

**1. DP Essentials**  
Dynamic Programming has three key ingredients:  
- **Optimal Substructure:** Problem can be divided into smaller optimal subproblems.  
- **Overlapping Subproblems:** Repeated subproblems can be reused.  
- **Memoization/Tabulation:** Store subproblem results to avoid recalculations.

---

**2. DP vs Divide and Conquer**  
- **Overlap:** DP reuses overlapping subproblems; D&C solves independent ones.  
- **Reuse:** DP stores results, D&C recomputes them.  
**Example:**  
- DP → Fibonacci sequence  
- D&C → Merge Sort

---

**3. Principle of Optimality**  
A problem satisfies this principle if its optimal solution contains optimal solutions to its subproblems.  
**Example:** Shortest Path Problem (e.g., Dijkstra’s algorithm).

---

**4. Memoization**  
**Memoization:** Top-down DP that caches recursive results.  
**Tabulation:** Bottom-up DP that builds a solution iteratively using tables.

---

**5. Branch and Bound Idea**  
Branch and Bound explores solution space as a tree, using **bounding** to estimate the best possible value and **pruning** branches that can’t lead to better results.

---

## SECTION B – Algorithms & Recurrences

**6. Matrix Chain Multiplication**  
Given matrices: A₁(5×4), A₂(4×6), A₃(6×2), A₄(2×7)  

**Recurrence:**  
```
m[i,j] = 0, if i = j  
m[i,j] = min_{k=i to j-1} (m[i,k] + m[k+1,j] + p_{i-1}*p_k*p_j)
```
**Minimum scalar multiplications:** 158

---

**7. Longest Common Subsequence (X = "ABCDGH", Y = "AEDFHR")**  

**Recurrence:**  
```
LCS(i, j) = 0, if i=0 or j=0  
LCS(i, j) = 1 + LCS(i-1, j-1), if X[i] = Y[j]  
LCS(i, j) = max(LCS(i-1, j), LCS(i, j-1)), otherwise
```
**LCS length:** 3

---

**8. Optimal Binary Search Tree**  
Keys: {10, 20, 30}, p = {0.4, 0.3, 0.3}, q = 0  

**Formulations:**  
```
w[i,j] = sum(p[i..j])  
e[i,j] = min_{r=i to j} (e[i,r-1] + e[r+1,j] + w[i,j])
```
**Minimum expected search cost:** 1.7

---

**9. 0/1 Knapsack – Branch & Bound**  
W = 5; w = {2,3,4,5}; p = {3,4,5,6}  

**Fractional upper bound:**  
```
UB = current_value + (remaining_capacity * next_item_value/next_item_weight)
```
**Nodes:**  
Level 0 → (v=0, w=0, ub=10.5)  
Level 1 include item1 → (v=3, w=2, ub=9.33)  
Level 1 exclude item1 → (v=0, w=0, ub=9.0)

---

**10. TSP – Dynamic Programming (Held–Karp)**  

**Recurrence:**  
```
C[S, j] = min_{k ∈ S, k ≠ j} [C[S - {j}, k] + D[k][j]]
Final answer = min_{j ≠ 1} [C[{2,3,4}, j] + D[j][1]]
```
**Base Initialization:**  
C[{2},2] = D[1][2], C[{3},3] = D[1][3], C[{4},4] = D[1][4]
