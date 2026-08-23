# Striver A2Z DSA — Arrays Hard in Java

## Course Introduction

This guide is designed for learners who already have a strong foundation in C++ and want to master **Arrays (Hard)** problems from Striver's A2Z DSA Sheet using **Java** for placements. 

- All solutions are implemented in **Java**.
- Key language differences between **C++** and **Java** are highlighted for every problem.
- Explanations are written in simple, beginner-friendly **Hinglish** to make logic tracing intuitive.
- The focus is on recognizing underlying **patterns** (e.g., Two Pointer, Binary Search, Merge Sort modifications, Prefix Sum, HashMaps, Bitwise XOR) rather than memorizing code templates.

---

## What You Will Learn

*   Dynamic generation logic in grids (Pascal's Triangle).
*   Extended Boyer-Moore voting algorithms for multiple candidate thresholds ($> N/3$).
*   Advanced sorting and two-pointer variations (3 Sum, 4 Sum) with strict duplication handling.
*   HashMap range tracking with math prefix operations (Sum 0, XOR K).
*   Merge intervals operations using custom comparators.
*   In-place merges without helper arrays using Gap method.
*   Divide and conquer inversion counters and double range comparisons (Inversions, Reverse Pairs).
*   Dual directional traversal scans (Max Product Subarray).

---

## Problem List

| # | Problem | Main Pattern | Difficulty |
|---|---|---|---|
| 1 | [Pascal's Triangle I](#1-pascals-triangle-i) | Grid Math / Combination | Hard |
| 2 | [Majority Element-II](#2-majority-element-ii) | Boyer-Moore (Extended) | Hard |
| 3 | [3 Sum](#3-sum) | Sort + Two Pointer | Hard |
| 4 | [4 Sum](#4-sum) | Sort + Two Pointer | Hard |
| 5 | [Largest Subarray with Sum 0](#5-largest-subarray-with-sum-0) | Prefix Sum + HashMap | Hard |
| 6 | [Count Subarrays with Given XOR K](#6-count-subarrays-with-given-xor-k) | Prefix XOR + HashMap | Hard |
| 7 | [Merge Overlapping Subintervals](#7-merge-overlapping-subintervals) | Interval Sorting | Hard |
| 8 | [Merge Two Sorted Arrays Without Extra Space](#8-merge-two-sorted-arrays-without-extra-space) | Gap Method (Shell Sort) | Hard |
| 9 | [Find the Repeating and Missing Number](#9-find-the-repeating-and-missing-number) | Bitwise XOR / Maths | Hard |
| 10 | [Count Inversions](#10-count-inversions) | Merge Sort Modification | Hard |
| 11 | [Reverse Pairs](#11-reverse-pairs) | Merge Sort Modification | Hard |
| 12 | [Maximum Product Subarray in an Array](#12-maximum-product-subarray-in-an-array) | Prefix & Suffix Products | Hard |

---

## Table of Contents

- [1. Pascal's Triangle I](#1-pascals-triangle-i)
- [2. Majority Element-II](#2-majority-element-ii)
- [3. 3 Sum](#3-sum)
- [4. 4 Sum](#4-sum)
- [5. Largest Subarray with Sum 0](#5-largest-subarray-with-sum-0)
- [6. Count Subarrays with Given XOR K](#6-count-subarrays-with-given-xor-k)
- [7. Merge Overlapping Subintervals](#7-merge-overlapping-subintervals)
- [8. Merge Two Sorted Arrays Without Extra Space](#8-merge-two-sorted-arrays-without-extra-space)
- [9. Find the Repeating and Missing Number](#9-find-the-repeating-and-missing-number)
- [10. Count Inversions](#10-count-inversions)
- [11. Reverse Pairs](#11-reverse-pairs)
- [12. Maximum Product Subarray in an Array](#12-maximum-product-subarray-in-an-array)

---

# 1. Pascal's Triangle I

---

## 1️⃣ Problem Statement
Given an integer `numRows`, return the first `numRows` of Pascal's triangle.

In Pascal's triangle, each number is the sum of the two numbers directly above it.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume `numRows` size ka Pascal's Triangle row-by-row create karna hai aur use `List<List<Integer>>` format me return karna hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `numRows = 5` | `[[1],[1,1],[1,2,1],[1,3,3,1],[1,4,6,4,1]]` |

---

## 4️⃣ Constraints
* `1 <= numRows <= 30`
* For `numRows = 30`, values can fit within standard Java `int`.

---

## 5️⃣ C++ → Java Connection
C++ uses nested vectors `vector<vector<int>>`, Java uses nested lists `List<List<Integer>>`.

C++:
```cpp
vector<vector<int>> ans;
vector<int> row;
ans.push_back(row);
```
Java:
```java
List<List<Integer>> ans = new ArrayList<>();
List<Integer> row = new ArrayList<>();
ans.add(row);
```

---

## 6️⃣ Solution Approaches

### Optimal (Dynamic Generation)
Row `i` create karne ke liye uske adjacent values `prevRow.get(j-1) + prevRow.get(j)` ko sum up karte jao.
```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> ans = new ArrayList<>();
        
        for (int i = 0; i < numRows; i++) {
            List<Integer> row = new ArrayList<>();
            for (int j = 0; j <= i; j++) {
                if (j == 0 || j == i) {
                    row.add(1);
                } else {
                    List<Integer> prevRow = ans.get(i - 1);
                    row.add(prevRow.get(j - 1) + prevRow.get(j));
                }
            }
            ans.add(row);
        }
        return ans;
    }
}
```
* **Time Complexity**: $O(\text{numRows}^2)$ (double loop bounds check)
* **Space Complexity**: $O(1)$ auxiliary space (ignoring output nested list memory)

---

## 7️⃣ Dry Run
* `numRows = 3`
* `i = 0`: `row = [1]`, `ans = [[1]]`
* `i = 1`: `row = [1, 1]`, `ans = [[1], [1,1]]`
* `i = 2`: `j=0` -> `1`. `j=1` -> `prevRow(index 1) -> prevRow.get(0) + prevRow.get(1) = 1 + 1 = 2`. `j=2` -> `1`. `row = [1, 2, 1]`, `ans = [[1], [1,1], [1,2,1]]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Be careful with `ans.get(i - 1)` bounds check. Ensure index variables check positive values before access.

---

## 9️⃣ Key Takeaways
Building lists sequentially allows direct accesses to elements from `i - 1` row indexes to build cell values.

---

# 2. Majority Element-II

---

## 1️⃣ Problem Statement
Given an integer array `nums` of size `N`, find all elements that appear more than `⌊ N/3 ⌋` times.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array ke andar aise saare elements find karne hain jo array size ke `1/3` se zyada (`> N/3` times) baar aate hain. Aise elements maximum **do** hi ho sakte hain.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[3,2,3]` | `[3]` |
| `[1,2]` | `[1,2]` |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 5 * 10^4`
* `-10^9 <= nums[i] <= 10^9`

---

## 5️⃣ C++ → Java Connection
List declarations comparisons.

C++:
```cpp
vector<int> ans;
```
Java:
```java
List<Integer> ans = new ArrayList<>();
```

---

## 6️⃣ Solution Approaches

### Better
Use HashMap to store element counts.
```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;

class Solution {
    public List<Integer> majorityElement(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        List<Integer> ans = new ArrayList<>();
        int limit = nums.length / 3;
        
        for (int x : nums) {
            map.put(x, map.getOrDefault(x, 0) + 1);
        }
        for (int key : map.keySet()) {
            if (map.get(key) > limit) {
                ans.add(key);
            }
        }
        return ans;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$

### Optimal (Extended Boyer-Moore Voting Algorithm)
Maintain two candidates and their counters.
```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> majorityElement(int[] nums) {
        int n = nums.length;
        int cand1 = 0, cand2 = 0;
        int count1 = 0, count2 = 0;
        
        // Step 1: Find potential candidates
        for (int x : nums) {
            if (x == cand1) {
                count1++;
            } else if (x == cand2) {
                count2++;
            } else if (count1 == 0) {
                cand1 = x;
                count1 = 1;
            } else if (count2 == 0) {
                cand2 = x;
                count2 = 1;
            } else {
                count1--;
                count2--;
            }
        }
        
        // Step 2: Validate candidates
        count1 = 0;
        count2 = 0;
        for (int x : nums) {
            if (x == cand1) count1++;
            else if (x == cand2) count2++;
        }
        
        List<Integer> ans = new ArrayList<>();
        int limit = n / 3;
        if (count1 > limit) ans.add(cand1);
        if (count2 > limit) ans.add(cand2);
        
        return ans;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

---

## 7️⃣ Dry Run
* Input: `[1, 2]`
* `x = 1`: `count1 = 0` -> `cand1 = 1, count1 = 1`
* `x = 2`: `count2 = 0` -> `cand2 = 2, count2 = 1`
* Validation checks: count for `1` is 1, count for `2` is 1. Limit = 2/3 = 0. Both counts $> 0$, returns `[1, 2]`.

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Initialize candidate variables safely. Check candidates with `else if` chains so the same element is not allocated to both candidates.

---

## 9️⃣ Key Takeaways
Extension of Boyer-Moore supports up to $K-1$ elements occurring $> N/K$ times by maintaining $K-1$ tracking variables.

---

# 3. 3 Sum

---

## 1️⃣ Problem Statement
Given an integer array `nums`, return all unique triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

The solution set must not contain duplicate triplets.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me se teen aise elements find karne hain jinka sum exactly `0` ho. Dhyaan rahe ki triplets unique hone chahiye (koi duplicate matching set output me nahi hona chahiye).

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[-1,0,1,2,-1,-4]` | `[[-1,-1,2],[-1,0,1]]` |

---

## 4️⃣ Constraints
* `3 <= nums.length <= 3000`
* `-10^5 <= nums[i] <= 10^5`

---

## 5️⃣ C++ → Java Connection
List handling comparisons.

C++:
```cpp
vector<vector<int>> ans;
sort(nums.begin(), nums.end());
```
Java:
```java
List<List<Integer>> ans = new ArrayList<>();
Arrays.sort(nums);
```

---

## 6️⃣ Solution Approaches

### Better
Fix two elements, use a HashSet to check if the third element `-(nums[i] + nums[j])` exists.
```java
import java.util.*;

class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Set<List<Integer>> st = new HashSet<>();
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            Set<Integer> hashset = new HashSet<>();
            for (int j = i + 1; j < n; j++) {
                int third = -(nums[i] + nums[j]);
                if (hashset.contains(third)) {
                    List<Integer> temp = Arrays.asList(nums[i], nums[j], third);
                    Collections.sort(temp);
                    st.add(temp);
                }
                hashset.add(nums[j]);
            }
        }
        return new ArrayList<>(st);
    }
}
```
* **Time Complexity**: $O(N^2 \log(\text{unique triplets}))$
* **Space Complexity**: $O(N)$ (hashset storage)

### Optimal (Sort + Two Pointer)
Sort the array. Fix pointer `i`. Use two pointers `left` and `right` for the remaining elements, skipping duplicate values on iterations.
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(nums);
        int n = nums.length;
        
        for (int i = 0; i < n - 2; i++) {
            // Skip duplicates for 'i'
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            
            int left = i + 1;
            int right = n - 1;
            
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum == 0) {
                    ans.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    left++;
                    right--;
                    // Skip duplicates for 'left'
                    while (left < right && nums[left] == nums[left - 1]) left++;
                    // Skip duplicates for 'right'
                    while (left < right && nums[right] == nums[right + 1]) right--;
                } else if (sum < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }
        return ans;
    }
}
```
* **Time Complexity**: $O(N \log N + N^2) = O(N^2)$
* **Space Complexity**: $O(1)$ auxiliary space

---

## 7️⃣ Dry Run
* Input: `[-1, 0, 1, 2, -1, -4]`. Sorted: `[-4, -1, -1, 0, 1, 2]`
* `i = 0 (-4)`: `left = 1 (-1), right = 5 (2)` -> `sum = -3 < 0` -> `left = 2 (-1)` -> `sum = -3 < 0` -> `left = 3 (0)` -> `sum = -2 < 0` -> loop ends.
* `i = 1 (-1)`: `left = 2 (-1), right = 5 (2)` -> `sum = 0` -> add `[-1, -1, 2]`. `left = 3 (0), right = 4 (1)` (after skipping duplicates) -> `sum = 0` -> add `[-1, 0, 1]`.
* Output: `[[-1, -1, 2], [-1, 0, 1]]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Use `Arrays.asList(a, b, c)` to easily construct `List<Integer>` objects. Avoid duplicate array insertions.

---

## 9️⃣ Key Takeaways
Sorting simplifies duplicates elimination because identical elements group adjacent to each other.

---

# 4. 4 Sum

---

## 1️⃣ Problem Statement
Given an array `nums` of `N` integers and an integer `target`, return all unique quadruplets `[nums[a], nums[b], nums[c], nums[d]]` such that their sum is equal to `target`.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me se char elements find karne hain jinka sum exactly `target` ke barabar ho. Quadruplets unique hone chahiye.

---

## 3️⃣ Example / Test Cases
| Input | Target | Output |
|---|---|---|
| `[1,0,-1,0,-2,2]` | 0 | `[[-2,-1,1,2],[-2,0,0,2],[-1,0,0,1]]` |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 200`
* `-10^9 <= nums[i] <= 10^9`
* `-10^9 <= target <= 10^9`

---

## 5️⃣ C++ → Java Connection
Use `long` variable allocations to prevent integer ranges overflow during comparisons in sum logic.

C++:
```cpp
long long sum = nums[i] + nums[j];
```
Java:
```java
long sum = (long)nums[i] + nums[j];
```

---

## 6️⃣ Solution Approaches

### Optimal (Sort + 2 Loops + Two Pointer)
Fix first two pointers `i` and `j`. Use `left` and `right` pointers for remaining search range, skipping duplicates.
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        List<List<Integer>> ans = new ArrayList<>();
        Arrays.sort(nums);
        int n = nums.length;
        
        for (int i = 0; i < n - 3; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            for (int j = i + 1; j < n - 2; j++) {
                if (j > i + 1 && nums[j] == nums[j - 1]) continue;
                
                int left = j + 1;
                int right = n - 1;
                
                while (left < right) {
                    long sum = (long)nums[i] + nums[j] + nums[left] + nums[right];
                    if (sum == target) {
                        ans.add(Arrays.asList(nums[i], nums[j], nums[left], nums[right]));
                        left++;
                        right--;
                        while (left < right && nums[left] == nums[left - 1]) left++;
                        while (left < right && nums[right] == nums[right + 1]) right--;
                    } else if (sum < target) {
                        left++;
                    } else {
                        right--;
                    }
                }
            }
        }
        return ans;
    }
}
```
* **Time Complexity**: $O(N^3)$ (nested loops + two-pointer scan)
* **Space Complexity**: $O(1)$ auxiliary space

---

## 7️⃣ Dry Run
Same logic pattern as 3 Sum. Outer pointers bounds fixed, internal scan shifts left/right references according to sums differences with target values.

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Must cast the first summation operand to `(long)` (e.g., `(long)nums[i]`) otherwise standard `int` addition occurs first, leading to integer overflow before conversion to long.

---

## 9️⃣ Key Takeaways
Using `long` prevents standard arithmetic overflow bugs during extreme targets evaluations.

---

# 5. Largest Subarray with Sum 0

---

## 1️⃣ Problem Statement
Given an array `arr` of size `N`, find the length of the largest subarray with sum equal to `0`.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me se longest contiguous subarray find karna hai jiska sum exactly `0` ho.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[15, -2, 2, -8, 1, 7, 10, 23]` | `5` (Subarray: `[-2, 2, -8, 1, 7]`) |

---

## 4️⃣ Constraints
* `1 <= arr.length <= 10^5`

---

## 5️⃣ C++ → Java Connection
C++: `unordered_map<int, int>`
Java: `HashMap<Integer, Integer>`

C++:
```cpp
unordered_map<int, int> mp;
```
Java:
```java
HashMap<Integer, Integer> map = new HashMap<>();
```

---

## 6️⃣ Solution Approaches

### Optimal (Prefix Sum + HashMap)
Cumulative prefix sum maintain karo. Agar prefix sum pehle map me exist karta hai at index `j`, to index range `[j+1, i]` ka sum `0` hoga.
```java
import java.util.HashMap;

class Solution {
    public int maxLen(int arr[], int n) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int sum = 0;
        int maxLen = 0;
        
        for (int i = 0; i < n; i++) {
            sum += arr[i];
            
            if (sum == 0) {
                maxLen = i + 1;
            } else {
                if (map.containsKey(sum)) {
                    maxLen = Math.max(maxLen, i - map.get(sum));
                } else {
                    map.put(sum, i);
                }
            }
        }
        return maxLen;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$

---

## 7️⃣ Dry Run
Input: `[15, -2, 2]`
* `i = 0`: `sum = 15` -> `map.put(15, 0)`
* `i = 1`: `sum = 13` -> `map.put(13, 1)`
* `i = 2`: `sum = 15` -> `15` exists at index `0` -> `maxLen = Math.max(0, 2 - 0) = 2`
* Output: `2`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Only store the first occurrence of prefix sum in the map to ensure we subtract from the leftmost index, maximizing the length of the subarray.

---

## 9️⃣ Key Takeaways
Prefix sum collisions identify subarray ranges that sum to 0.

---

# 6. Count Subarrays with Given XOR K

---

## 1️⃣ Problem Statement
Given an array of integers `A` and an integer `B`, find the total number of subarrays having bitwise XOR sum equal to `B`.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me se aise total subarrays count karne hain jin ke elements ka XOR product exactly `B` ke barabar ho.

---

## 3️⃣ Example / Test Cases
| Input | Target (B) | Output |
|---|---|---|
| `[4, 2, 2, 6, 4]` | 6 | `4` |

---

## 4️⃣ Constraints
* `1 <= A.length <= 10^5`
* `1 <= A[i], B <= 10^9`

---

## 5️⃣ C++ → Java Connection
HashMap increments comparing C++ syntax.

C++:
```cpp
mpp[xr]++;
```
Java:
```java
map.put(xr, map.getOrDefault(xr, 0) + 1);
```

---

## 6️⃣ Solution Approaches

### Optimal (Prefix XOR + HashMap)
If $Y \oplus X = xr$, then $Y = xr \oplus X$. We search for prefix XOR value `xr ^ B` in the map.
```java
import java.util.HashMap;

class Solution {
    public int solve(int[] A, int B) {
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, 1); // Base case initialization
        int xr = 0;
        int count = 0;
        
        for (int x : A) {
            xr ^= x;
            int rem = xr ^ B;
            if (map.containsKey(rem)) {
                count += map.get(rem);
            }
            map.put(xr, map.getOrDefault(xr, 0) + 1);
        }
        return count;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$

---

## 7️⃣ Dry Run
* Input: `[4, 2, 2]`, `B = 6`
* `map = {0: 1}`
* `x = 4`: `xr = 4`. `rem = 4 ^ 6 = 2` (no) -> `map = {0:1, 4:1}`
* `x = 2`: `xr = 6`. `rem = 6 ^ 6 = 0` (exists, count = 1) -> `map = {0:1, 4:1, 6:1}`
* `x = 2`: `xr = 4`. `rem = 4 ^ 6 = 2` (no) -> `map = {0:1, 4:2, 6:1}`
* Output count: `1` (Subarray: `[4, 2]` has XOR = 6).

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Do not forget the map baseline setup `map.put(0, 1)`.

---

## 9️⃣ Key Takeaways
XOR operations properties support linear lookups when mapped using frequency HashMaps.

---

# 7. Merge Overlapping Subintervals

---

## 1️⃣ Problem Statement
Given an array of `intervals` where `intervals[i] = [start_i, end_i]`, merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the input intervals.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume list of intervals diye hain, jo overlapping intervals hain unhe merge karke ek final array of non-overlapping intervals generate karna hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[[1,3],[2,6],[8,10],[15,18]]` | `[[1,6],[8,10],[15,18]]` |

---

## 4️⃣ Constraints
* `1 <= intervals.length <= 10^4`
* `intervals[i].length == 2`

---

## 5️⃣ C++ → Java Connection
Sorting custom comparator logic.

C++:
```cpp
sort(intervals.begin(), intervals.end());
```
Java:
```java
Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
```

---

## 6️⃣ Solution Approaches

### Optimal (Interval Sorting)
Sort elements by start coordinates. Add first interval to output. Scan through remaining:
- If current start <= end of last element in list, merge: `end = Math.max(end, current_end)`.
- Else, insert current interval as new element.
```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals.length <= 1) return intervals;
        
        // Sort intervals based on starting values
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        
        List<int[]> ans = new ArrayList<>();
        int[] currentInterval = intervals[0];
        ans.add(currentInterval);
        
        for (int[] interval : intervals) {
            int currentEnd = currentInterval[1];
            int nextStart = interval[0];
            int nextEnd = interval[1];
            
            if (nextStart <= currentEnd) {
                currentInterval[1] = Math.max(currentEnd, nextEnd); // Merge
            } else {
                currentInterval = interval; // Move to next interval
                ans.add(currentInterval);
            }
        }
        return ans.toArray(new int[ans.size()][]);
    }
}
```
* **Time Complexity**: $O(N \log N)$ (sorting cost)
* **Space Complexity**: $O(N)$ (for list conversion output)

---

## 7️⃣ Dry Run
* Input: `[[1,3],[2,6],[8,10]]`
* Sort: remains same.
* `current = [1, 3]`. `ans = [[1, 3]]`
* `interval = [2, 6]`: `2 <= 3` -> merge -> `current[1] = Math.max(3, 6) = 6`. `ans` holds `[1, 6]`
* `interval = [8, 10]`: `8 > 6` -> `current = [8, 10]`. `ans.add([8, 10])`
* Output: `[[1,6],[8,10]]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Use lambda expressions `(a, b) -> Integer.compare(a[0], b[0])` to sort 2D array coordinates cleanly. Use `list.toArray(new int[size][])` to convert lists back to matrices.

---

## 9️⃣ Key Takeaways
Sorting elements by start times ensures we only need to compare adjacent intervals to find overlaps.

---

# 8. Merge Two Sorted Arrays Without Extra Space

---

## 1️⃣ Problem Statement
Given two sorted arrays `arr1[]` and `arr2[]` of sizes `N` and `M` respectively, merge them in sorted order without using any extra space.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Do sorted arrays ko bina extra helper space use kiye merge karna hai taaki `arr1` me small elements aur `arr2` me remaining larger elements sorted order me aa jayein.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `arr1 = [1,3,5,7]`, `arr2 = [0,2,6,8,9]` | `arr1 = [0,1,2,3]`, `arr2 = [5,6,7,8,9]` |

---

## 4️⃣ Constraints
* `1 <= n, m <= 5 * 10^4`

---

## 5️⃣ C++ → Java Connection
Inline swaps.

C++:
```cpp
swap(arr1[left], arr2[right]);
```
Java:
```java
int temp = arr1[left];
arr1[left] = arr2[right];
arr2[right] = temp;
```

---

## 6️⃣ Solution Approaches

### Optimal (Gap Method / Shell Sort variant)
Compute `gap = ceil((n+m)/2)`. Run loop swapping elements at gap. Divide gap by 2. Repeat until gap = 0.
```java
class Solution {
    public void merge(int[] arr1, int[] arr2, int n, int m) {
        int len = n + m;
        int gap = (len / 2) + (len % 2);
        
        while (gap > 0) {
            int left = 0;
            int right = left + gap;
            
            while (right < len) {
                // Case 1: left in arr1, right in arr2
                if (left < n && right >= n) {
                    swapIfGreater(arr1, arr2, left, right - n);
                }
                // Case 2: both in arr2
                else if (left >= n) {
                    swapIfGreater(arr2, arr2, left - n, right - n);
                }
                // Case 3: both in arr1
                else {
                    swapIfGreater(arr1, arr1, left, right);
                }
                left++;
                right++;
            }
            if (gap == 1) break;
            gap = (gap / 2) + (gap % 2);
        }
    }
    
    private void swapIfGreater(int[] arr1, int[] arr2, int ind1, int ind2) {
        if (arr1[ind1] > arr2[ind2]) {
            int temp = arr1[ind1];
            arr1[ind1] = arr2[ind2];
            arr2[ind2] = temp;
        }
    }
}
```
* **Time Complexity**: $O((N + M) \log(N + M))$
* **Space Complexity**: $O(1)$ (in-place swaps)

---

## 7️⃣ Dry Run
Standard shell sort iterations pattern. Elements are shifted across the boundary indices between both arrays using the gap pointer offset.

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Ensure the index conversion `right - n` or `left - n` is used when pointers cross into `arr2` range boundaries.

---

## 9️⃣ Key Takeaways
Shell sort gap technique sorts partitioned segments in place without allocating auxiliary arrays.

---

# 9. Find the Repeating and Missing Number

---

## 1️⃣ Problem Statement
Given an unsorted array of size `N` of positive integers. One number 'A' from set `{1, 2, ..., N}` is missing and one number 'B' occurs twice in array. Find these two numbers.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume `1` se `N` numbers ka ek unsorted array diya hai jisme ek number missing hai aur ek number repeat ho raha hai. Hume repeating aur missing elements find karne hain.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[3, 1, 2, 5, 3]` | `Repeating = 3, Missing = 4` |

---

## 4️⃣ Constraints
* `2 <= N <= 10^5`

---

## 5️⃣ C++ → Java Connection
Bitwise calculations remain identical.

C++:
```cpp
int bitNo = 0;
```
Java:
```java
int bitNo = 0;
```

---

## 6️⃣ Solution Approaches

### Optimal (Mathematical Equations)
Let repeating be `X`, missing be `Y`.
Calculate differences using actual sum and squared sums.
```java
class Solve {
    int[] findTwoElement(int arr[], int n) {
        long N = n;
        long sumN = N * (N + 1) / 2;
        long sumNSqr = N * (N + 1) * (2 * N + 1) / 6;
        
        long sumA = 0;
        long sumASqr = 0;
        for (int x : arr) {
            sumA += x;
            sumASqr += (long) x * x;
        }
        
        // Eq 1: X - Y
        long val1 = sumA - sumN;
        
        // Eq 2: X^2 - Y^2
        long val2 = sumASqr - sumNSqr;
        
        // Eq 3: X + Y = (X^2 - Y^2) / (X - Y)
        long val3 = val2 / val1;
        
        long X = (val1 + val3) / 2;
        long Y = val3 - X;
        
        return new int[]{(int)X, (int)Y};
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

---

## 7️⃣ Dry Run
* Input: `[3, 1, 2, 5, 3]`, `n = 5`
* `sumN = 15`, `sumNSqr = 55`
* `sumA = 14`, `sumASqr = 48`
* `val1 = 14 - 15 = -1` (i.e. `X - Y = -1`)
* `val2 = 48 - 55 = -7` (i.e. `X^2 - Y^2 = -7`)
* `val3 = -7 / -1 = 7` (i.e. `X + Y = 7`)
* `X = (-1 + 7) / 2 = 3` (Repeating)
* `Y = 7 - 3 = 4` (Missing)
* Output: `[3, 4]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Must cast multiplication `(long) x * x` to prevent integer overflow before long assignment.

---

## 9️⃣ Key Takeaways
Mathematical prefix summation equations resolve duplicates and omissions issues without needing temporary space.

---

# 10. Count Inversions

---

## 1️⃣ Problem Statement
Given an array, count the number of inversions in the array. Two elements `arr[i]` and `arr[j]` form an inversion if `i < j` and `arr[i] > arr[j]`.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array ke andar aise pairs ki count find karni hai jinke indices `i < j` ho par elements values `arr[i] > arr[j]` ho.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[2, 4, 1, 3, 5]` | `3` (Pairs: `(2,1)`, `(4,1)`, `(4,3)`) |

---

## 4️⃣ Constraints
* `1 <= arr.length <= 10^5`

---

## 5️⃣ C++ → Java Connection
Modified Merge Sort implementation.

C++:
```cpp
// Merge sort algorithm modification
```
Java:
```java
// Merge sort implementation with recursive count aggregation
```

---

## 6️⃣ Solution Approaches

### Optimal (Merge Sort modification)
Divide array using merge sort. During merge step, if `arr[left] > arr[right]`, then all elements to the right of `left` in the left subarray are also greater than `arr[right]`. Add `mid - left + 1` to counts.
```java
class Solution {
    public long inversionCount(long arr[], long N) {
        return mergeSort(arr, 0, (int)(N - 1));
    }
    
    private long mergeSort(long[] arr, int low, int high) {
        long count = 0;
        if (low < high) {
            int mid = low + (high - low) / 2;
            count += mergeSort(arr, low, mid);
            count += mergeSort(arr, mid + 1, high);
            count += merge(arr, low, mid, high);
        }
        return count;
    }
    
    private long merge(long[] arr, int low, int mid, int high) {
        long[] temp = new long[high - low + 1];
        int left = low;
        int right = mid + 1;
        int k = 0;
        long count = 0;
        
        while (left <= mid && right <= high) {
            if (arr[left] <= arr[right]) {
                temp[k++] = arr[left++];
            } else {
                temp[k++] = arr[right++];
                count += (mid - left + 1); // Key step
            }
        }
        
        while (left <= mid) {
            temp[k++] = arr[left++];
        }
        while (right <= high) {
            temp[k++] = arr[right++];
        }
        
        for (int i = 0; i < temp.length; i++) {
            arr[low + i] = temp[i];
        }
        return count;
    }
}
```
* **Time Complexity**: $O(N \log N)$
* **Space Complexity**: $O(N)$ (temporary array utilized during merging)

---

## 7️⃣ Dry Run
* Subarrays: `[2, 4]` and `[1, 3]`
* Merge pointers: `left = 0 (2)`, `right = 2 (1)`
* `2 > 1` -> count increments by `mid - left + 1` -> `1 - 0 + 1 = 2` (pairs: `(2,1)` and `(4,1)`).
* `left` advances, elements merge.

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Ensure count variables are `long` type because total inversions can be up to $N(N-1)/2$, which exceeds integer limit for $N = 10^5$.

---

## 9️⃣ Key Takeaways
Merge sort's sorted subarrays property allows counting multiple inversion pairs in $O(1)$ operations per element.

---

# 11. Reverse Pairs

---

## 1️⃣ Problem Statement
Given an integer array `nums`, return the number of reverse pairs in the array. A reverse pair is a pair `(i, j)` where `i < j` and `nums[i] > 2 * nums[j]`.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me aise pairs count karne hain jisme index `i < j` ho aur `nums[i] > 2 * nums[j]` ho.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[1,3,2,3,1]` | `2` (Pairs: `(3,1)` at indices `(1,4)` and `(3,1)` at indices `(3,4)`) |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 5 * 10^4`
* `-2^31 <= nums[i] <= 2^31 - 1`

---

## 5️⃣ C++ → Java Connection
Similar structure to count inversions.

C++:
```cpp
// Count reverse pairs step prior to merging
```
Java:
```java
// Count reverse pairs step prior to merging
```

---

## 6️⃣ Solution Approaches

### Optimal (Merge Sort variant)
Before merging two sorted halves in the merge sort step, count elements from first half that satisfy `nums[left] > 2 * nums[right]` by keeping a pointer to the second half.
```java
class Solution {
    public int reversePairs(int[] nums) {
        return mergeSort(nums, 0, nums.length - 1);
    }
    
    private int mergeSort(int[] nums, int low, int high) {
        int count = 0;
        if (low < high) {
            int mid = low + (high - low) / 2;
            count += mergeSort(nums, low, mid);
            count += mergeSort(nums, mid + 1, high);
            count += countPairs(nums, low, mid, high);
            merge(nums, low, mid, high);
        }
        return count;
    }
    
    private int countPairs(int[] nums, int low, int mid, int high) {
        int count = 0;
        int right = mid + 1;
        for (int i = low; i <= mid; i++) {
            while (right <= high && nums[i] > 2 * (long)nums[right]) {
                right++;
            }
            count += (right - (mid + 1));
        }
        return count;
    }
    
    private void merge(int[] nums, int low, int mid, int high) {
        int[] temp = new int[high - low + 1];
        int left = low;
        int right = mid + 1;
        int k = 0;
        
        while (left <= mid && right <= high) {
            if (nums[left] <= nums[right]) {
                temp[k++] = nums[left++];
            } else {
                temp[k++] = nums[right++];
            }
        }
        while (left <= mid) temp[k++] = nums[left++];
        while (right <= high) temp[k++] = nums[right++];
        
        for (int i = 0; i < temp.length; i++) {
            nums[low + i] = temp[i];
        }
    }
}
```
* **Time Complexity**: $O(N \log N)$
* **Space Complexity**: $O(N)$

---

## 7️⃣ Dry Run
* Subarrays: `[3]` and `[1]`
* `nums[left] = 3`, `nums[right] = 1`. `3 > 2 * 1` (true) -> count increments by 1.
* Merge completes.

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Must cast calculation `2 * (long)nums[right]` to long to avoid integer overflow issues when elements values are close to `Integer.MAX_VALUE`.

---

## 9️⃣ Key Takeaways
Splitting inversion-like verification step from standard merge operation keeps code correct and maintains $O(N \log N)$ performance.

---

# 12. Maximum Product Subarray in an Array

---

## 1️⃣ Problem Statement
Given an integer array `nums`, find a contiguous non-empty subarray within the array that has the largest product, and return the product.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array ke continuous elements ka maximum product (multiplication output) find karna hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[2,3,-2,4]` | `6` (Subarray: `[2, 3]`) |
| `[-2,0,-1]` | `0` |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 2 * 10^4`
* `-10 <= nums[i] <= 10`

---

## 5️⃣ C++ → Java Connection
Math max comparisons.

C++:
```cpp
maxProduct = max(maxProduct, prefix);
```
Java:
```java
maxProduct = Math.max(maxProduct, prefix);
```

---

## 6️⃣ Solution Approaches

### Optimal (Prefix and Suffix Products)
Running prefix and suffix products scans. If we encounter a `0`, reset the product accumulator to `1`.
```java
class Solution {
    public int maxProduct(int[] nums) {
        int n = nums.length;
        double prefix = 1;
        double suffix = 1;
        double maxProduct = Integer.MIN_VALUE;
        
        for (int i = 0; i < n; i++) {
            if (prefix == 0) prefix = 1;
            if (suffix == 0) suffix = 1;
            
            prefix *= nums[i];
            suffix *= nums[n - 1 - i];
            
            maxProduct = Math.max(maxProduct, Math.max(prefix, suffix));
        }
        return (int) maxProduct;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

---

## 7️⃣ Dry Run
* Input: `[2, 3, -2, 4]`
* `i = 0`: `prefix = 2`, `suffix = 4` -> `max = 4`
* `i = 1`: `prefix = 6`, `suffix = -8` -> `max = 6`
* `i = 2`: `prefix = -12`, `suffix = -24` -> `max = 6`
* `i = 3`: `prefix = -48`, `suffix = -48` -> `max = 6`
* Output: `6`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Use `double` for calculation variables to prevent overflow during intermediate computations if needed, though standard integer range limits are acceptable under constraints.

---

## 9️⃣ Key Takeaways
Maximum product subarray always lies either at the prefix side or the suffix side of the array unless interrupted by a 0.

---

# 🎯 Final Striver Arrays Hard Checklist

- [ ] Pascal's Triangle I
- [ ] Majority Element-II
- [ ] 3 Sum
- [ ] 4 Sum
- [ ] Largest Subarray with Sum 0
- [ ] Count Subarrays with Given XOR K
- [ ] Merge Overlapping Subintervals
- [ ] Merge Two Sorted Arrays Without Extra Space
- [ ] Find the Repeating and Missing Number
- [ ] Count Inversions
- [ ] Reverse Pairs
- [ ] Maximum Product Subarray in an Array

---

# 🧠 Patterns Covered

- [ ] Math Combinations
- [ ] Boyer-Moore Voting Algorithm
- [ ] Sort + Two Pointer
- [ ] Hashing + Prefix Operations
- [ ] Custom Comparator Sorting
- [ ] Shell Sort Gap Method
- [ ] Mathematical Equations
- [ ] Merge Sort Modifications (Inversions counting)
- [ ] Prefix & Suffix Products
