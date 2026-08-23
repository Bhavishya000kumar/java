# Chapter 17 — Recursion ⭐⭐

### 1. What is it?
Recursion is a process in which a method calls itself directly or indirectly. It solves a larger problem by breaking it down into smaller sub-problems.

### 2. Why do I need it for placements?
Recursion is the basis for advanced DSA techniques like backtracking, tree traversals, graphs, and dynamic programming. Standard mass-recruiter rounds check fundamentals like printing subsets, subsequences, and generating combinations.

### 3. C++ → Java Comparison
The execution flow is identical. The key differences concern **parameter passing** and memory management:
*   **No Ampersand Pass-By-Reference:**
    *   C++: `void solve(int idx, vector<int>& ds)` (modifications to `ds` are direct).
    *   Java: `void solve(int idx, ArrayList<Integer> ds)` (passes a copy of reference by value; elements can be mutated, but replacing `ds = new ArrayList<>()` won't update caller reference).
*   **Heap Allocation:** Java stores all objects and collections in heap, while C++ can allocate structures on stack frame directly.

---

### 4. Basic Problems

#### Q1: Sum of First N Numbers (Functional vs Parameterized)
```java
// Functional Recursion
public int sum(int n) {
    if (n == 0) return 0;
    return n + sum(n - 1);
}
```

#### Q2: Reverse an Array using Recursion
```java
public void reverse(int[] arr, int l, int r) {
    if (l >= r) return;
    int temp = arr[l];
    arr[l] = arr[r];
    arr[r] = temp;
    reverse(arr, l + 1, r - 1);
}
```

#### Q3: Fibonacci Number
```java
public int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

---

### 5. Core DSA Recursion Patterns

#### Pattern 1: Pick / Not Pick (Include / Exclude)
*Used to generate all subsequences/subsets of a set.*

*   **C++ Logic:**
    ```cpp
    void getSubsequences(int idx, vector<int>& ds, int arr[], int n) {
        if (idx == n) {
            print(ds);
            return;
        }
        // Include (Pick)
        ds.push_back(arr[idx]);
        getSubsequences(idx + 1, ds, arr, n);
        
        // Exclude (Not Pick / Backtrack)
        ds.pop_back();
        getSubsequences(idx + 1, ds, arr, n);
    }
    ```
*   **Java Equivalent/Code:**
    ```java
    import java.util.ArrayList;
    import java.util.List;

    public class Subsequences {
        public void getSubsequences(int idx, List<Integer> ds, int[] arr, List<List<Integer>> ans) {
            if (idx == arr.length) {
                ans.add(new ArrayList<>(ds)); // Deep copy is required!
                return;
            }
            // Include (Pick)
            ds.add(arr[idx]);
            getSubsequences(idx + 1, ds, arr, ans);
            
            // Exclude (Not Pick / Backtrack)
            ds.remove(ds.size() - 1); // Removes last element
            getSubsequences(idx + 1, ds, arr, ans);
        }
    }
    ```
*   **Dry Run & Call Stack:**
    For `arr = {1, 2}`:
    1. `idx=0`: ds adds `1`, calls `idx=1`
    2. `idx=1`: ds adds `2`, calls `idx=2`
    3. `idx=2`: Base Case. Copy of ds `[1, 2]` added to `ans`. Returns.
    4. Backtracks at `idx=1`: Removes `2`. Calls `idx=2`.
    5. `idx=2`: Base Case. Copy of ds `[1]` added to `ans`. Returns.
*   **Complexity:** Time: $O(2^N)$, Space: $O(N)$ (recursion auxiliary stack depth).
*   **Common Java Mistake:** Writing `ans.add(ds)` instead of `ans.add(new ArrayList<>(ds))`. If you pass `ds` directly, you are passing the reference. When `ds` undergoes changes or becomes empty during backtracking, all items stored inside `ans` will also turn empty.

---

#### Pattern 2: Basic Permutations Generation
*Generates all unique orderings of an array.*

*   **C++ Logic:**
    ```cpp
    void recurPermute(int idx, vector<int>& nums, vector<vector<int>>& ans) {
        if (idx == nums.size()) {
            ans.push_back(nums);
            return;
        }
        for (int i = idx; i < nums.size(); i++) {
            swap(nums[idx], nums[i]);
            recurPermute(idx + 1, nums, ans);
            swap(nums[idx], nums[i]); // backtrack
        }
    }
    ```
*   **Java Code:**
    ```java
    import java.util.ArrayList;
    import java.util.List;

    public class Permutations {
        public List<List<Integer>> permute(int[] nums) {
            List<List<Integer>> ans = new ArrayList<>();
            solve(0, nums, ans);
            return ans;
        }

        private void solve(int idx, int[] nums, List<List<Integer>> ans) {
            if (idx == nums.length) {
                List<Integer> ds = new ArrayList<>();
                for (int x : nums) ds.add(x);
                ans.add(ds);
                return;
            }
            for (int i = idx; i < nums.length; i++) {
                swap(nums, idx, i);
                solve(idx + 1, nums, ans);
                swap(nums, idx, i); // backtrack
            }
        }

        private void swap(int[] nums, int i, int j) {
            int temp = nums[i];
            nums[i] = nums[j];
            nums[j] = temp;
        }
    }
    ```
*   **Complexity:** Time: $O(N! \times N)$, Space: $O(N)$

---

### 10. Common Mistakes
*   **Infinite Recursion (Stack Overflow):** Missing base case or not modifying boundary arguments.
*   **Reference Modification Trap:** Forgetting to remove last inserted element during backtracking (e.g. missing `ds.remove(ds.size() - 1)`).

### 11. Interview Point
*   **Why does recursion cause StackOverflowError?**
    Each recursive call creates a new stack frame containing local variables and return addresses. If recursion is too deep (or infinite), stack memory runs out, triggering `StackOverflowError`.

### 12. Quick Revision
*   Include/Exclude: `ds.add(val)` $\rightarrow$ Recurse $\rightarrow$ `ds.remove(ds.size() - 1)`.
*   Result tracking: Always create deep copies (`new ArrayList<>(ds)`) when storing active recursion variables.
