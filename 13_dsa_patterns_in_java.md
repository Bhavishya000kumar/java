# Chapter 13 — DSA Patterns in Java

### 1. What is it?
DSA patterns are standardized structures used to solve families of algorithmic problems. This chapter provides reusable Java templates for common DSA strategies directly mapped from C++.

### 2. Why do I need it for placements?
Having a clear template in mind speeds up implementation during timed coding tests, preventing syntax errors under pressure.

---

### Pattern 1: Two Pointer

#### Description
Used for searching pairs in a sorted array or reversing elements.

*   **C++ Template:**
    ```cpp
    int left = 0, right = n - 1;
    while (left < right) {
        int sum = arr[left] + arr[right];
        if (sum == target) return {left, right};
        else if (sum < target) left++;
        else right--;
    }
    ```
*   **Java Template:**
    ```java
    int left = 0;
    int right = arr.length - 1;
    while (left < right) {
        int sum = arr[left] + arr[right];
        if (sum == target) {
            return new int[]{left, right}; // Note inline initialization
        } else if (sum < target) {
            left++;
        } else {
            right--;
        }
    }
    ```
*   **Important Java Syntax Difference:**
    Returning inline anonymous arrays in Java requires the syntax `new int[]{val1, val2}`. Unlike C++, you cannot return `{left, right}` directly.

---

### Pattern 2: Sliding Window (Variable Size)

#### Description
Used to find subarray properties matching a condition (e.g. longest subarray with sum $\le K$).

*   **C++ Template:**
    ```cpp
    int left = 0, max_len = 0, current_sum = 0;
    for (int right = 0; right < n; right++) {
        current_sum += arr[right];
        while (current_sum > k) {
            current_sum -= arr[left];
            left++;
        }
        max_len = max(max_len, right - left + 1);
    }
    ```
*   **Java Template:**
    ```java
    int left = 0, maxLen = 0, currentSum = 0;
    for (int right = 0; right < arr.length; right++) {
        currentSum += arr[right];
        while (currentSum > k) {
            currentSum -= arr[left];
            left++;
        }
        maxLen = Math.max(maxLen, right - left + 1);
    }
    ```
*   **Important Java Syntax Difference:**
    C++ `max()` helper becomes `Math.max()`. Use of `arr.length` instead of size variable `n`.

---

### Pattern 3: Prefix Sum

#### Description
Precalculating dynamic ranges of queries.

*   **C++ Template:**
    ```cpp
    vector<int> pref(n, 0);
    pref[0] = arr[0];
    for (int i = 1; i < n; i++) {
        pref[i] = pref[i - 1] + arr[i];
    }
    ```
*   **Java Template:**
    ```java
    int[] pref = new int[arr.length];
    pref[0] = arr[0];
    for (int i = 1; i < arr.length; i++) {
        pref[i] = pref[i - 1] + arr[i];
    }
    ```
*   **Important Java Syntax Difference:**
    C++ `vector` initialization is replaced by primitive array declarations on the heap (`new int[arr.length]`).

---

### Pattern 4: Hashing & Frequency Count

#### Description
Counting occurrences of elements in a list.

*   **C++ Template:**
    ```cpp
    unordered_map<int, int> mp;
    for (int num : arr) {
        mp[num]++;
    }
    ```
*   **Java Template:**
    ```java
    HashMap<Integer, Integer> map = new HashMap<>();
    for (int num : arr) {
        map.put(num, map.getOrDefault(num, 0) + 1);
    }
    ```
*   **Important Java Syntax Difference:**
    C++ maps auto-initialize non-existent keys to `0` when `mp[num]++` runs. Java will throw a `NullPointerException` if you do `map.put(num, map.get(num) + 1)` when the key is missing. **Always use `map.getOrDefault(key, 0)`.**

---

### Pattern 5: Binary Search (Standard)

#### Description
Finding an element's index in sorted collections.

*   **C++ Template:**
    ```cpp
    int low = 0, high = n - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    ```
*   **Java Template:**
    ```java
    int low = 0;
    int high = arr.length - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    ```

---

### Pattern 6: Kadane's Algorithm

#### Description
Finding the maximum sum subarray.

*   **C++ Template:**
    ```cpp
    int max_sum = INT_MIN, curr_sum = 0;
    for (int num : arr) {
        curr_sum += num;
        max_sum = max(max_sum, curr_sum);
        if (curr_sum < 0) curr_sum = 0;
    }
    ```
*   **Java Template:**
    ```java
    int maxSum = Integer.MIN_VALUE;
    int currSum = 0;
    for (int num : arr) {
        currSum += num;
        maxSum = Math.max(maxSum, currSum);
        if (currSum < 0) {
            currSum = 0;
        }
    }
    ```

---

### Pattern 7: Binary Search on Answer (Optimization)

#### Description
Finds boundary matching monotonic criteria (e.g. minimum capacity, speed, or distance limit).

*   **C++ Template:**
    ```cpp
    int low = minVal, high = maxVal, ans = -1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (isValid(arr, mid, target)) {
            ans = mid;
            high = mid - 1; // Try to search left for smaller minimum
        } else {
            low = mid + 1;
        }
    }
    ```
*   **Java Template:**
    ```java
    int low = minVal;
    int high = maxVal;
    int ans = -1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (isValid(arr, mid, target)) {
            ans = mid;
            high = mid - 1; // Min optimization
        } else {
            low = mid + 1;
        }
    }
    ```

---

### Pattern 8: Recursion (Backtracking/Include-Exclude)

#### Description
Generates combinations, permutations, subsets, or subsequences.

*   **C++ Template (Pick / Not Pick):**
    ```cpp
    void solve(int idx, vector<int>& ds, vector<int>& arr) {
        if (idx == arr.size()) {
            process(ds);
            return;
        }
        ds.push_back(arr[idx]); // Pick
        solve(idx + 1, ds, arr);
        ds.pop_back(); // Backtrack
        solve(idx + 1, ds, arr); // Not Pick
    }
    ```
*   **Java Template (Pick / Not Pick):**
    ```java
    public void solve(int idx, List<Integer> ds, int[] arr, List<List<Integer>> ans) {
        if (idx == arr.length) {
            ans.add(new ArrayList<>(ds)); // Deep copy reference values
            return;
        }
        ds.add(arr[idx]); // Pick
        solve(idx + 1, ds, arr, ans);
        ds.remove(ds.size() - 1); // Backtrack / Exclude
        solve(idx + 1, ds, arr, ans); // Not Pick
    }
    ```
*   **Important Java Syntax Difference:**
    In C++, `ds` is passed by reference and copied to target matrix output cleanly. In Java, adding a reference directly with `ans.add(ds)` will cause issues because `ds` will end up being modified. You **must** create a new instance duplicate copy via `new ArrayList<>(ds)`.
