# Striver A2Z DSA — Arrays Medium in Java

## 🎯 Course Goal

This guide is designed for learners who already have a strong foundation in C++ and want to master **Arrays (Medium)** problems from Striver's A2Z DSA Sheet using **Java** for placements. 

- All solutions are implemented in **Java**.
- Key language differences between **C++** and **Java** are highlighted for every problem.
- Explanations are written in simple, beginner-friendly **Hinglish** to make logic tracing intuitive.
- The focus is on recognizing underlying **patterns** (e.g., Two Pointer, Sliding Window, Prefix Sum, Hashing) rather than memorizing code templates.

---

## 📚 Problem List

| # | Problem | Main Pattern | Difficulty |
|---|---|---|---|
| 1 | [Two Sum](#1-two-sum) | Hashing | Medium |
| 2 | [Sort an array of 0's, 1's and 2's](#2-sort-an-array-of-0s-1s-and-2s) | Dutch National Flag | Medium |
| 3 | [Majority Element-I](#3-majority-element-i) | Moore's Voting | Medium |
| 4 | [Kadane's Algorithm — Maximum Subarray Sum](#4-kadanes-algorithm--maximum-subarray-sum) | Dynamic Programming | Medium |
| 5 | [Print Subarray with Maximum Subarray Sum](#5-print-subarray-with-maximum-subarray-sum) | Index Tracking | Medium |
| 6 | [Stock Buy and Sell](#6-stock-buy-and-sell) | Greedy / Two Pointer | Medium |
| 7 | [Rearrange Array Elements by Sign](#7-rearrange-array-elements-by-sign) | Two Pointer | Medium |
| 8 | [Next Permutation](#8-next-permutation) | Lexicographical Check | Medium |
| 9 | [Leaders in an Array](#9-leaders-in-an-array) | Reverse Scanning | Medium |
| 10 | [Longest Consecutive Sequence in an Array](#10-longest-consecutive-sequence-in-an-array) | HashSet Traversal | Medium |
| 11 | [Set Matrix Zeroes](#11-set-matrix-zeroes) | In-place Matrix Marking | Medium |
| 12 | [Rotate Matrix by 90 Degrees](#12-rotate-matrix-by-90-degrees) | Transpose & Reverse | Medium |
| 13 | [Print the Matrix in Spiral Manner](#13-print-the-matrix-in-spiral-manner) | Boundary Traversal | Medium |
| 14 | [Count Subarrays with Given Sum](#14-count-subarrays-with-given-sum) | Prefix Sum + HashMap | Medium |

---

## 📑 Table of Contents

- [1. Two Sum](#1-two-sum)
- [2. Sort an array of 0's, 1's and 2's](#2-sort-an-array-of-0s-1s-and-2s)
- [3. Majority Element-I](#3-majority-element-i)
- [4. Kadane's Algorithm — Maximum Subarray Sum](#4-kadanes-algorithm--maximum-subarray-sum)
- [5. Print Subarray with Maximum Subarray Sum](#5-print-subarray-with-maximum-subarray-sum)
- [6. Stock Buy and Sell](#6-stock-buy-and-sell)
- [7. Rearrange Array Elements by Sign](#7-rearrange-array-elements-by-sign)
- [8. Next Permutation](#8-next-permutation)
- [9. Leaders in an Array](#9-leaders-in-an-array)
- [10. Longest Consecutive Sequence in an Array](#10-longest-consecutive-sequence-in-an-array)
- [11. Set Matrix Zeroes](#11-set-matrix-zeroes)
- [12. Rotate Matrix by 90 Degrees](#12-rotate-matrix-by-90-degrees)
- [13. Print the Matrix in Spiral Manner](#13-print-the-matrix-in-spiral-manner)
- [14. Count Subarrays with Given Sum](#14-count-subarrays-with-given-sum)

---

# 1. Two Sum

---

## 1️⃣ Problem Statement
Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me do aise elements find karne hain jinka sum `target` ke equal ho, aur unke indices return karne hain.

---

## 3️⃣ Example / Test Cases
| Input | Target | Output |
|---|---:|---|
| `[2,7,11,15]` | 9 | `[0,1]` |
| `[3,2,4]` | 6 | `[1,2]` |

---

## 4️⃣ Constraints
* `2 <= nums.length <= 10^4`
* `-10^9 <= nums[i] <= 10^9`
* `-10^9 <= target <= 10^9`

---

## 5️⃣ C++ → Java Connection
C++ uses `unordered_map`, Java uses `HashMap`.

C++:
```cpp
unordered_map<int, int> mp;
if (mp.find(rem) != mp.end()) { ... }
```
Java:
```java
HashMap<Integer, Integer> mp = new HashMap<>();
if (mp.containsKey(rem)) { ... }
```

---

## 6️⃣ Solution Approaches

### Brute Force
Nested loops use karke check karo agar `nums[i] + nums[j] == target` hai.
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{};
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$

### Optimal (Hashing)
Map me element aur uske index ko store karte jao. Har element par check karo ki kya `target - nums[i]` pehle se map me present hai.
```java
import java.util.HashMap;

class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int rem = target - nums[i];
            if (map.containsKey(rem)) {
                return new int[]{map.get(rem), i};
            }
            map.put(nums[i], i);
        }
        return new int[]{};
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$ (Map storage cost)

---

## 7️⃣ Dry Run
* Input: `[3,2,4]`, `target = 6`
* `i = 0 (3)`: `rem = 6 - 3 = 3` -> map does not contain 3 -> `map.put(3, 0)`
* `i = 1 (2)`: `rem = 6 - 2 = 4` -> map does not contain 4 -> `map.put(2, 1)`
* `i = 2 (4)`: `rem = 6 - 4 = 2` -> map contains 2 -> returns `[1, 2]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Java maps require object wrapper classes like `Integer`. Avoid using `int` inside collections generics.

---

## 9️⃣ Key Takeaways
For index retrieval, Hashing is the optimal approach. Two-pointer approach is only useful if array is sorted or sorting is acceptable, but sorting alters original indices.

---

# 2. Sort an array of 0's, 1's and 2's

---

## 1️⃣ Problem Statement
Given an array `nums` containing only `0`s, `1`s, and `2`s, sort the array in-place.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me 0s, 1s, aur 2s ko ek sequence me sort karna hai bina extra space use kiye aur in-place updates ke sath.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[2,0,2,1,1,0]` | `[0,0,1,1,2,2]` |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 300`
* `nums[i]` is either `0`, `1`, or `2`.

---

## 5️⃣ C++ → Java Connection
Pointer manipulation remains the same. C++ can use `std::swap`, Java uses manual inline swap.

C++:
```cpp
swap(nums[low], nums[mid]);
```
Java:
```java
int temp = nums[low];
nums[low] = nums[mid];
nums[mid] = temp;
```

---

## 6️⃣ Solution Approaches

### Brute Force
Call standard sorting `Arrays.sort()`.
```java
class Solution {
    public void sortColors(int[] nums) {
        java.util.Arrays.sort(nums);
    }
}
```
* **Time Complexity**: $O(N \log N)$
* **Space Complexity**: $O(1)$

### Better
Count number of 0s, 1s, and 2s, and overwrite array in second pass.
```java
class Solution {
    public void sortColors(int[] nums) {
        int c0 = 0, c1 = 0, c2 = 0;
        for (int x : nums) {
            if (x == 0) c0++;
            else if (x == 1) c1++;
            else c2++;
        }
        int i = 0;
        while (c0-- > 0) nums[i++] = 0;
        while (c1-- > 0) nums[i++] = 1;
        while (c2-- > 0) nums[i++] = 2;
    }
}
```
* **Time Complexity**: $O(N)$ (requires two passes)
* **Space Complexity**: $O(1)$

### Optimal (Dutch National Flag Algorithm)
Maintain three pointers: `low`, `mid`, and `high`.
- `[0 ... low-1]` holds 0s.
- `[low ... mid-1]` holds 1s.
- `[high+1 ... n-1]` holds 2s.
```java
class Solution {
    public void sortColors(int[] nums) {
        int low = 0;
        int mid = 0;
        int high = nums.length - 1;
        
        while (mid <= high) {
            if (nums[mid] == 0) {
                int temp = nums[low];
                nums[low] = nums[mid];
                nums[mid] = temp;
                low++;
                mid++;
            } else if (nums[mid] == 1) {
                mid++;
            } else {
                int temp = nums[high];
                nums[high] = nums[mid];
                nums[mid] = temp;
                high--;
            }
        }
    }
}
```
* **Time Complexity**: $O(N)$ (single pass)
* **Space Complexity**: $O(1)$

---

## 7️⃣ Dry Run
* Input: `[2, 0, 1]`
* `low = 0, mid = 0, high = 2`
* `nums[mid] == 2` -> swap `mid` and `high` -> `[1, 0, 2]`, `high = 1`
* `nums[mid] == 1` -> `mid = 1`
* `nums[mid] == 0` -> swap `low` and `mid` -> `[0, 1, 2]`, `low = 1, mid = 2`
* Loop breaks because `mid (2) > high (1)`.

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Be careful with `mid` increment when swapping with `high`. The incoming element from `high` could be 0, 1 or 2, so `mid` must not be incremented immediately.

---

## 9️⃣ Key Takeaways
DNF algorithm is a classic partition strategy. Extremely useful for sorting a 3-valued domain in a single pass.

---

# 3. Majority Element-I

---

## 1️⃣ Problem Statement
Given an array `nums` of size `N`, return the majority element. The majority element is the element that appears more than `⌊N / 2⌋` times.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me woh element find karna hai jo array ke size se half se zyada (`> N/2` times) baar aata hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[3,2,3]` | `3` |
| `[2,2,1,1,1,2,2]` | `2` |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 5 * 10^4`
* `-10^9 <= nums[i] <= 10^9`

---

## 5️⃣ C++ → Java Connection
C++: `map` or sorting logic. Java equivalents are `HashMap` or `Arrays.sort()`.

C++:
```cpp
sort(nums.begin(), nums.end());
```
Java:
```java
Arrays.sort(nums);
```

---

## 6️⃣ Solution Approaches

### Better
Use a HashMap to store count frequencies.
```java
import java.util.HashMap;

class Solution {
    public int majorityElement(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int limit = nums.length / 2;
        for (int x : nums) {
            map.put(x, map.getOrDefault(x, 0) + 1);
            if (map.get(x) > limit) {
                return x;
            }
        }
        return -1;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$

### Optimal (Boyer-Moore Voting Algorithm)
Maintain a `candidate` and a `count` variable. Count cancels matching pairs.
```java
class Solution {
    public int majorityElement(int[] nums) {
        int candidate = 0;
        int count = 0;
        
        for (int x : nums) {
            if (count == 0) {
                candidate = x;
                count = 1;
            } else if (x == candidate) {
                count++;
            } else {
                count--;
            }
        }
        return candidate;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

---

## 7️⃣ Dry Run
* Input: `[2, 2, 1, 1, 1, 2, 2]`
* `x = 2`: `count = 0` -> `candidate = 2`, `count = 1`
* `x = 2`: `2 == 2` -> `count = 2`
* `x = 1`: `1 != 2` -> `count = 1`
* `x = 1`: `1 != 2` -> `count = 0`
* `x = 1`: `count = 0` -> `candidate = 1`, `count = 1`
* `x = 2`: `2 != 1` -> `count = 0`
* `x = 2`: `count = 0` -> `candidate = 2`, `count = 1`
* Return: `2`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Boyer-Moore assumes a majority element always exists. If not guaranteed, we must verify the candidate in a second pass.

---

## 9️⃣ Key Takeaways
Voting algorithm utilizes the principle of cancellation to solve majority count in $O(N)$ time and $O(1)$ space.

---

# 4. Kadane's Algorithm — Maximum Subarray Sum

---

## 1️⃣ Problem Statement
Given an integer array `nums`, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me se koi ek continuous section (subarray) chunn-na hai jiska sum sabse bada (maximum) ho.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[-2,1,-3,4,-1,2,1,-5,4]` | `6` (Subarray: `[4,-1,2,1]`) |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 10^5`
* `-10^4 <= nums[i] <= 10^4`

---

## 5️⃣ C++ → Java Connection
Standard optimization logic. C++ `INT_MIN` translates to Java `Integer.MIN_VALUE`.

C++:
```cpp
int max_sum = INT_MIN;
```
Java:
```java
int maxSum = Integer.MIN_VALUE;
```

---

## 6️⃣ Solution Approaches

### Brute Force
Check all possible subarrays using three nested loops.
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = Integer.MIN_VALUE;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int sum = 0;
                for (int k = i; k <= j; k++) {
                    sum += nums[k];
                }
                max = Math.max(max, sum);
            }
        }
        return max;
    }
}
```
* **Time Complexity**: $O(N^3)$
* **Space Complexity**: $O(1)$

### Better
Optimized nested loop tracking running sum.
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = Integer.MIN_VALUE;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            int sum = 0;
            for (int j = i; j < n; j++) {
                sum += nums[j];
                max = Math.max(max, sum);
            }
        }
        return max;
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$

### Optimal (Kadane's Algorithm)
If the cumulative sum becomes negative, reset the sum to 0. Keep tracking the maximum sum.
```java
class Solution {
    public int maxSubArray(int[] nums) {
        int max = Integer.MIN_VALUE;
        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
            max = Math.max(max, sum);
            if (sum < 0) {
                sum = 0;
            }
        }
        return max;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

---

## 7️⃣ Dry Run
* Input: `[-2, 1, -3, 4]`
* `i = 0 (-2)`: `sum = -2`, `max = -2` -> `sum < 0` -> `sum = 0`
* `i = 1 (1)`: `sum = 1`, `max = Math.max(-2, 1) = 1`
* `i = 2 (-3)`: `sum = -2`, `max = 1` -> `sum < 0` -> `sum = 0`
* `i = 3 (4)`: `sum = 4`, `max = Math.max(1, 4) = 4`
* Output: `4`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Initializing `max` with `0` instead of `Integer.MIN_VALUE`. If array contains only negative elements, returning `0` is incorrect.

---

## 9️⃣ Key Takeaways
Kadane's algorithm leverages running prefix sum transitions. Resetting negative sums works because adding a negative sum can never increase a subsequent subarray sum.

---

# 5. Print Subarray with Maximum Subarray Sum

---

## 1️⃣ Problem Statement
Given an integer array `nums`, print/return the actual elements of the contiguous subarray which has the largest sum.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume Kadane's sum calculation ke sath-sath woh exact subarray trace karke return ya print karna hai jiska sum sabse bada hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[-2,1,-3,4,-1,2,1,-5,4]` | `[4,-1,2,1]` |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 10^5`

---

## 5️⃣ C++ → Java Connection
Uses index variable markers to copy a range of elements. C++ `vector` range assignment vs Java `Arrays.copyOfRange()`.

C++:
```cpp
vector<int> ans(nums.begin() + start, nums.begin() + end + 1);
```
Java:
```java
int[] ans = java.util.Arrays.copyOfRange(nums, start, end + 1);
```

---

## 6️⃣ Solution Approaches

### Optimal (Index Tracking in Kadane's)
Track index ranges `start` and `end` whenever `max` sum is updated.
```java
class Solution {
    public int[] maxSubArrayIndices(int[] nums) {
        int max = Integer.MIN_VALUE;
        int sum = 0;
        int start = 0;
        int ansStart = -1;
        int ansEnd = -1;
        
        for (int i = 0; i < nums.length; i++) {
            if (sum == 0) start = i; // Store starting boundary of subarray candidate
            
            sum += nums[i];
            
            if (sum > max) {
                max = sum;
                ansStart = start;
                ansEnd = i;
            }
            
            if (sum < 0) {
                sum = 0;
            }
        }
        
        // Copy subarray elements
        int[] subarray = new int[ansEnd - ansStart + 1];
        int idx = 0;
        for (int i = ansStart; i <= ansEnd; i++) {
            subarray[idx++] = nums[i];
        }
        return subarray;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$ auxiliary space (ignoring output subarray storage)

---

## 7️⃣ Dry Run
* Input: `[-2, 1, -3, 4]`
* `i = 0 (-2)`: `sum = 0` -> `start = 0`. `sum = -2`. `max = -2, ansStart = 0, ansEnd = 0`. `sum < 0` -> `sum = 0`
* `i = 1 (1)`: `sum = 0` -> `start = 1`. `sum = 1`. `sum > max` -> `max = 1, ansStart = 1, ansEnd = 1`
* `i = 2 (-3)`: `sum = -2` -> `sum < 0` -> `sum = 0`
* `i = 3 (4)`: `sum = 0` -> `start = 3`. `sum = 4`. `sum > max` -> `max = 4, ansStart = 3, ansEnd = 3`
* Resulting indices range: `[3, 3]` -> Subarray: `[4]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Ensure the subarray allocation array has size `ansEnd - ansStart + 1`.

---

## 9️⃣ Key Takeaways
Keeping track of variables when `sum` transitions from `0` to active is key to capture boundaries in linear time algorithms.

---

# 6. Stock Buy and Sell

---

## 1️⃣ Problem Statement
You are given an array `prices` where `prices[i]` is the price of a given stock on the `i-th` day. Choose a single day to buy one stock and choose a different day in the future to sell that stock to maximize profit. Return the maximum profit.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume stock buy karne ka best day aur sell karne ka best future day select karna hai, taaki maximum profit ho sake.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[7,1,5,3,6,4]` | `5` (Buy at index 1: price = 1, Sell at index 4: price = 6) |
| `[7,6,4,3,1]` | `0` (No profit possible) |

---

## 4️⃣ Constraints
* `1 <= prices.length <= 10^5`
* `0 <= prices[i] <= 10^4`

---

## 5️⃣ C++ → Java Connection
Standard min-max values comparison. C++ `min()` and `max()` vs Java `Math.min()` and `Math.max()`.

C++:
```cpp
minPrice = min(minPrice, prices[i]);
```
Java:
```java
minPrice = Math.min(minPrice, prices[i]);
```

---

## 6️⃣ Solution Approaches

### Brute Force
Check every possible buy day and corresponding future sell day.
```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        int n = prices.length;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int profit = prices[j] - prices[i];
                maxProfit = Math.max(maxProfit, profit);
            }
        }
        return maxProfit;
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$

### Optimal (Greedy)
Keep track of the minimum price seen so far. At each step, calculate potential profit and update max profit.
```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;
        
        for (int i = 0; i < prices.length; i++) {
            if (prices[i] < minPrice) {
                minPrice = prices[i];
            } else {
                int profit = prices[i] - minPrice;
                maxProfit = Math.max(maxProfit, profit);
            }
        }
        return maxProfit;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

---

## 7️⃣ Dry Run
* Input: `[7, 1, 5, 3, 6]`
* `prices[0] = 7`: `minPrice = 7`
* `prices[1] = 1`: `1 < 7` -> `minPrice = 1`
* `prices[2] = 5`: `5 > 1` -> `profit = 5 - 1 = 4`, `maxProfit = 4`
* `prices[3] = 3`: `3 > 1` -> `profit = 3 - 1 = 2`, `maxProfit = 4`
* `prices[4] = 6`: `6 > 1` -> `profit = 6 - 1 = 5`, `maxProfit = Math.max(4, 5) = 5`
* Output: `5`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Initializing `minPrice` with `0` instead of `Integer.MAX_VALUE` which fails logic comparisons.

---

## 9️⃣ Key Takeaways
Greedy approach works because we only need to scan forward, tracking our global minimum price to maximize the differences.

---

# 7. Rearrange Array Elements by Sign

---

## 1️⃣ Problem Statement
You are given a 0-indexed integer array `nums` of even length containing an equal number of positive and negative integers. Rearrange the elements of `nums` such that the modified array follows:
1. Every consecutive pair of integers have opposite signs.
2. For all integers with the same sign, the relative order in which they were present in `nums` is preserved.
3. The rearranged array begins with a positive integer.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array elements ko alternate positive aur negative signs ke set me rearrange karna hai, positive se start karte hue. Wording: elements ka relative original order alter nahi hona chahiye.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[3,1,-2,-5,2,-4]` | `[3,-2,1,-5,2,-4]` |

---

## 4️⃣ Constraints
* `2 <= nums.length <= 2 * 10^5` (even length)
* `nums` contains equal number of positive and negative elements.

---

## 5️⃣ C++ → Java Connection
C++: `vector<int> ans(n)`
Java: `int[] ans = new int[n]`

C++:
```cpp
vector<int> ans(n, 0);
```
Java:
```java
int[] ans = new int[nums.length];
```

---

## 6️⃣ Solution Approaches

### Brute Force
Extract positive elements and negative elements into two separate lists, then merge them alternately.
```java
import java.util.ArrayList;

class Solution {
    public int[] rearrangeArray(int[] nums) {
        ArrayList<Integer> pos = new ArrayList<>();
        ArrayList<Integer> neg = new ArrayList<>();
        
        for (int x : nums) {
            if (x > 0) pos.add(x);
            else neg.add(x);
        }
        
        int[] ans = new int[nums.length];
        int p = 0, n = 0;
        for (int i = 0; i < nums.length; i++) {
            if (i % 2 == 0) {
                ans[i] = pos.get(p++);
            } else {
                ans[i] = neg.get(n++);
            }
        }
        return ans;
    }
}
```
* **Time Complexity**: $O(N)$ (requires 2 full passes)
* **Space Complexity**: $O(N)$

### Optimal (Single Pass Two Pointer)
Maintain `posIndex = 0` and `negIndex = 1`. Place elements directly.
```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
        int n = nums.length;
        int[] ans = new int[n];
        int posIndex = 0;
        int negIndex = 1;
        
        for (int i = 0; i < n; i++) {
            if (nums[i] > 0) {
                ans[posIndex] = nums[i];
                posIndex += 2;
            } else {
                ans[negIndex] = nums[i];
                negIndex += 2;
            }
        }
        return ans;
    }
}
```
* **Time Complexity**: $O(N)$ (single pass)
* **Space Complexity**: $O(N)$ (for the result array)

---

## 7️⃣ Dry Run
* Input: `[3, -2, 1, -5]`
* `posIndex = 0`, `negIndex = 1`
* `i = 0 (3 > 0)`: `ans[0] = 3`, `posIndex = 2`
* `i = 1 (-2 < 0)`: `ans[1] = -2`, `negIndex = 3`
* `i = 2 (1 > 0)`: `ans[2] = 1`, `posIndex = 4`
* `i = 3 (-5 < 0)`: `ans[3] = -5`, `negIndex = 5`
* Output: `[3, -2, 1, -5]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Ensure pointers increment by 2 (`posIndex += 2`) to alternate positions.

---

## 9️⃣ Key Takeaways
Pre-allocating indices for positives and negatives allows in-place insertions directly without needing separate list storage structures.

---

# 8. Next Permutation

---

## 1️⃣ Problem Statement
Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers. If no such arrangement is possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array elements se banne wala lexicographically agla permutation/sequence find karna hai. Agar array decreasing sorted hai to sabse chota sequence (reverse order) output dena hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[1,2,3]` | `[1,3,2]` |
| `[3,2,1]` | `[1,2,3]` |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 100`
* `0 <= nums[i] <= 100`

---

## 5️⃣ C++ → Java Connection
C++ has `next_permutation` built-in inside STL. In Java, this algorithm must be implemented manually from scratch.

C++:
```cpp
next_permutation(nums.begin(), nums.end());
```
Java:
```java
// Manual implementation of the 3-step lexicographical algorithm
```

---

## 6️⃣ Solution Approaches

### Optimal (Manual Lexicographical Permutation Algorithm)
1. Find the first breakpoint `i` from the right where `nums[i] < nums[i+1]`.
2. If no breakpoint found (index = -1), reverse the array.
3. If breakpoint is found, find the smallest element to the right of the breakpoint that is strictly greater than `nums[breakpoint]`, swap them, and reverse the elements to the right of the breakpoint.
```java
class Solution {
    public void nextPermutation(int[] nums) {
        int n = nums.length;
        int ind = -1;
        
        // Step 1: Find the breakpoint
        for (int i = n - 2; i >= 0; i--) {
            if (nums[i] < nums[i + 1]) {
                ind = i;
                break;
            }
        }
        
        // Step 2: If no breakpoint, reverse entire array
        if (ind == -1) {
            reverse(nums, 0, n - 1);
            return;
        }
        
        // Step 3: Find the next greater element to swap
        for (int i = n - 1; i > ind; i--) {
            if (nums[i] > nums[ind]) {
                int temp = nums[i];
                nums[i] = nums[ind];
                nums[ind] = temp;
                break;
            }
        }
        
        // Step 4: Reverse the right half of the breakpoint
        reverse(nums, ind + 1, n - 1);
    }
    
    private void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

---

## 7️⃣ Dry Run
* Input: `[2, 1, 5, 4, 3, 0]`
* Step 1: scan right-to-left: `0->3->4->5->1` (drop point: `1 < 5` at index `1`) -> `ind = 1`
* Step 2: scan right to find element $> 1$: `0` (no), `3` (yes) -> swap `1` and `3` -> `[2, 3, 5, 4, 1, 0]`
* Step 3: reverse from `ind + 1 (index 2)` to end -> reverse `[5, 4, 1, 0]` -> `[0, 1, 4, 5]`
* Final Output: `[2, 3, 0, 1, 4, 5]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Remember to use a helper `reverse` function that modifies array parameters in-place in Java.

---

## 9️⃣ Key Takeaways
Without STL, next permutation follows a mathematical sequence logic: find drop point, swap with next larger right side element, and reverse suffix to minimize lexicographical values.

---

# 9. Leaders in an Array

---

## 1️⃣ Problem Statement
Given an array, find the leaders in the array. An element is a leader if it is greater than or equal to all the elements to its right side. The rightmost element is always a leader.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array me se leaders select karne hain. Leader woh elements hain jinse bada ya equal element unke right side me koi nahi ho.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[16, 17, 4, 3, 5, 2]` | `[17, 5, 2]` |

---

## 4️⃣ Constraints
* `1 <= arr.length <= 10^6`

---

## 5️⃣ C++ → Java Connection
List reversal operation comparison.

C++:
```cpp
reverse(ans.begin(), ans.end());
```
Java:
```java
Collections.reverse(ans);
```

---

## 6️⃣ Solution Approaches

### Brute Force
Double loop checking every element against all right side elements.
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<Integer> leaders(int[] arr) {
        ArrayList<Integer> ans = new ArrayList<>();
        int n = arr.length;
        for (int i = 0; i < n; i++) {
            boolean leader = true;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] > arr[i]) {
                    leader = false;
                    break;
                }
            }
            if (leader) ans.add(arr[i]);
        }
        return ans;
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$ (ignoring list memory)

### Optimal (Reverse Scan)
Traverse the array from right to left, keeping track of the maximum element seen so far.
```java
import java.util.ArrayList;
import java.util.Collections;

class Solution {
    public ArrayList<Integer> leaders(int[] arr) {
        ArrayList<Integer> ans = new ArrayList<>();
        int n = arr.length;
        int max = Integer.MIN_VALUE;
        
        for (int i = n - 1; i >= 0; i--) {
            if (arr[i] >= max) {
                ans.add(arr[i]);
                max = arr[i];
            }
        }
        // Since we traversed from right to left, we reverse list to keep original order
        Collections.reverse(ans);
        return ans;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$ auxiliary space

---

## 7️⃣ Dry Run
* Input: `[16, 17, 4, 3, 5, 2]`
* `max = -infinity`
* `i = 5 (2)`: `2 >= -inf` -> add `2`, `max = 2`
* `i = 4 (5)`: `5 >= 2` -> add `5`, `max = 5`
* `i = 3 (3)`: `3 >= 5` (false)
* `i = 2 (4)`: `4 >= 5` (false)
* `i = 1 (17)`: `17 >= 5` -> add `17`, `max = 17`
* `i = 0 (16)`: `16 >= 17` (false)
* List is `[2, 5, 17]`. Reversed: `[17, 5, 2]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Import `java.util.Collections` to use `Collections.reverse(list)`.

---

## 9️⃣ Key Takeaways
Scanning arrays from right-to-left simplifies tracking "all elements to the right" by maintaining a single cumulative maximum variable.

---

# 10. Longest Consecutive Sequence in an Array

---

## 1️⃣ Problem Statement
Given an unsorted array of integers `nums`, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in `O(N)` time.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume unsorted array ke andar consecutive (jaise 1, 2, 3, 4) elements ki sabse lambi sequence find karni hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[100, 4, 200, 1, 3, 2]` | `4` (Sequence: `[1, 2, 3, 4]`) |

---

## 4️⃣ Constraints
* `0 <= nums.length <= 10^5`
* `-10^9 <= nums[i] <= 10^9`

---

## 5️⃣ C++ → Java Connection
C++ uses `unordered_set`, Java uses `HashSet`.

C++:
```cpp
unordered_set<int> st(nums.begin(), nums.end());
```
Java:
```java
HashSet<Integer> st = new HashSet<>();
for (int x : nums) st.add(x);
```

---

## 6️⃣ Solution Approaches

### Better
Sort array first, then count consecutive elements.
```java
import java.util.Arrays;

class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums.length == 0) return 0;
        Arrays.sort(nums);
        int longest = 1;
        int current = 1;
        
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != nums[i - 1]) {
                if (nums[i] == nums[i - 1] + 1) {
                    current++;
                } else {
                    longest = Math.max(longest, current);
                    current = 1;
                }
            }
        }
        return Math.max(longest, current);
    }
}
```
* **Time Complexity**: $O(N \log N)$
* **Space Complexity**: $O(1)$

### Optimal (HashSet Traversal)
Insert all elements in a HashSet. For every element, check if it can be the starting point of a sequence (i.e. `nums[i]-1` is not in set). If yes, count the length of sequence.
```java
import java.util.HashSet;

class Solution {
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int x : nums) {
            set.add(x);
        }
        
        int longest = 0;
        
        for (int x : nums) {
            // Check if current element is the starting point of sequence
            if (!set.contains(x - 1)) {
                int currentNum = x;
                int currentStreak = 1;
                
                while (set.contains(currentNum + 1)) {
                    currentNum += 1;
                    currentStreak += 1;
                }
                longest = Math.max(longest, currentStreak);
            }
        }
        return longest;
    }
}
```
* **Time Complexity**: $O(N)$ (every element processed at most twice)
* **Space Complexity**: $O(N)$ (HashSet allocation)

---

## 7️⃣ Dry Run
* Input: `[100, 4, 200, 1, 3, 2]`
* Set: `[100, 4, 200, 1, 3, 2]`
* `x = 100`: `99` not in set -> start sequence `100` -> streak = 1.
* `x = 4`: `3` exists in set -> skip.
* `x = 1`: `0` not in set -> start sequence `1` -> `2` exists -> `3` exists -> `4` exists -> streak = 4.
* `x = 2`: `1` exists in set -> skip.
* Result: `4`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Double loops inside optimal code look like $O(N^2)$ but check constraints: the `while` loop only executes for starting elements, yielding linear time.

---

## 9️⃣ Key Takeaways
Using set constraints to identify "starting element candidates" prevents repetitive scans and reduces complexity to linear time.

---

# 11. Set Matrix Zeroes

---

## 1️⃣ Problem Statement
Given an `m x n` integer matrix, if an element is `0`, set its entire row and column to `0`'s. Do it in-place.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume matrix me agar koi element `0` dikhe, to uski puri row aur pure column ke saare elements ko `0` set karna hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[[1,1,1],[1,0,1],[1,1,1]]` | `[[1,0,1],[0,0,0],[1,0,1]]` |

---

## 4️⃣ Constraints
* `m == matrix.length`
* `n == matrix[0].length`
* `1 <= m, n <= 200`

---

## 5️⃣ C++ → Java Connection
Matrix sizes logic tracking.

C++:
```cpp
int m = matrix.size();
int n = matrix[0].size();
```
Java:
```java
int m = matrix.length;
int n = matrix[0].length;
```

---

## 6️⃣ Solution Approaches

### Better
Use separate helper arrays `row[m]` and `col[n]` to mark rows and columns containing zeroes.
```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        boolean[] row = new boolean[m];
        boolean[] col = new boolean[n];
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (matrix[i][j] == 0) {
                    row[i] = true;
                    col[j] = true;
                }
            }
        }
        
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (row[i] || col[j]) {
                    matrix[i][j] = 0;
                }
            }
        }
    }
}
```
* **Time Complexity**: $O(M \times N)$
* **Space Complexity**: $O(M + N)$

### Optimal (In-place Matrix Marking)
Use the first row and column of the matrix itself as the marking arrays, and a separate boolean variable `col0` for the first column.
```java
class Solution {
    public void setZeroes(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int col0 = 1;
        
        for (int i = 0; i < m; i++) {
            if (matrix[i][0] == 0) col0 = 0; // Check if first column has zero
            for (int j = 1; j < n; j++) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0;
                    matrix[0][j] = 0;
                }
            }
        }
        
        // Fill zeroes using markers from bottom-right up to cell (0,1)
        for (int i = m - 1; i >= 0; i--) {
            for (int j = n - 1; j >= 1; j--) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
            if (col0 == 0) {
                matrix[i][0] = 0;
            }
        }
    }
}
```
* **Time Complexity**: $O(M \times N)$
* **Space Complexity**: $O(1)$ (in-place)

---

## 7️⃣ Dry Run
* Input: `[[1,0],[1,1]]`
* `i = 0`: `matrix[0][0] != 0`. `j = 1`: `matrix[0][1] == 0` -> `matrix[0][0] = 0`, `matrix[0][1] = 0`
* `i = 1`: `matrix[1][0] != 0`. `j = 1`: `matrix[1][1] != 0`
* Second loops from back:
* `i = 1, j = 1`: `matrix[1][0] != 0` & `matrix[0][1] == 0` -> `matrix[1][1] = 0`
* `i = 0, j = 1`: `matrix[0][0] == 0` -> `matrix[0][1] = 0`
* Final: `[[1,0],[1,0]]` (wait: `matrix[0][0]` is modified during marker step). If `col0 = 1`, `matrix[0][0] = 0`. Correctly handles columns zero state.

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Incorrect loop bounds when resetting matrix using markers. Reversing traversal order ensures we do not overwrite active header markers.

---

## 9️⃣ Key Takeaways
Using matrix cells as temporary metadata flags is a powerful space saving technique for grid-based questions.

---

# 12. Rotate Matrix by 90 Degrees

---

## 1️⃣ Problem Statement
You are given an `n x n` 2D matrix representing an image, rotate the image by 90 degrees (clockwise) in-place.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume image matrix ko 90 degrees clockwise rotate karna hai. Rotate operation in-place hona chahiye.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[[1,2,3],[4,5,6],[7,8,9]]` | `[[7,4,1],[8,5,2],[9,6,3]]` |

---

## 4️⃣ Constraints
* `n == matrix.length == matrix[i].length`
* `1 <= n <= 20`

---

## 5️⃣ C++ → Java Connection
C++: `reverse(matrix[i].begin(), matrix[i].end())`
Java: manual row reversal loops.

C++:
```cpp
reverse(matrix[i].begin(), matrix[i].end());
```
Java:
```java
reverseRow(matrix[i]);
```

---

## 6️⃣ Solution Approaches

### Optimal (Transpose and Reverse)
1. Transpose the matrix (swap `matrix[i][j]` with `matrix[j][i]` for all $i < j$).
2. Reverse each row of the matrix.
```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        
        // Step 1: Transpose
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        
        // Step 2: Reverse each row
        for (int i = 0; i < n; i++) {
            int left = 0;
            int right = n - 1;
            while (left < right) {
                int temp = matrix[i][left];
                matrix[i][left] = matrix[i][right];
                matrix[i][right] = temp;
                left++;
                right--;
            }
        }
    }
}
```
* **Time Complexity**: $O(N^2)$ (Transpose: $O(N^2/2)$, Reverse: $O(N^2/2)$)
* **Space Complexity**: $O(1)$ (in-place modification)

---

## 7️⃣ Dry Run
Input: `[[1,2],[3,4]]`
* Transpose: swap `(0,1)` and `(1,0)` -> `[[1,3],[2,4]]`
* Reverse Row 0: `[1, 3]` -> `[3, 1]`
* Reverse Row 1: `[2, 4]` -> `[4, 2]`
* Output: `[[3,1],[4,2]]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Forgetting the $i < j$ (specifically `j = i + 1` in loop initialization) condition during transpose swaps, which swaps elements back to their original positions (double transposing).

---

## 9️⃣ Key Takeaways
Matrix rotation can be broken down into transpose and reverse, which simplifies complex coordinate math equations.

---

# 13. Print the Matrix in Spiral Manner

---

## 1️⃣ Problem Statement
Given an `m x n` matrix, return all elements of the matrix in spiral order.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume matrix elements ko spiral path (Top -> Right -> Bottom -> Left boundaries) me traverse karke print ya save karna hai.

---

## 3️⃣ Example / Test Cases
| Input | Output |
|---|---|
| `[[1,2,3],[4,5,6],[7,8,9]]` | `[1,2,3,6,9,8,7,4,5]` |

---

## 4️⃣ Constraints
* `m == matrix.length`
* `n == matrix[i].length`
* `1 <= m, n <= 10`

---

## 5️⃣ C++ → Java Connection
C++ uses `vector<int>`, Java uses `List<Integer>` / `ArrayList<Integer>`.

C++:
```cpp
vector<int> ans;
ans.push_back(x);
```
Java:
```java
ArrayList<Integer> ans = new ArrayList<>();
ans.add(x);
```

---

## 6️⃣ Solution Approaches

### Optimal (Boundary Traversal)
Maintain four boundary pointers: `top`, `bottom`, `left`, and `right`.
```java
import java.util.ArrayList;
import java.util.List;

class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<>();
        if (matrix == null || matrix.length == 0) return ans;
        
        int m = matrix.length;
        int n = matrix[0].length;
        int top = 0, bottom = m - 1;
        int left = 0, right = n - 1;
        
        while (top <= bottom && left <= right) {
            // 1. Traverse Left to Right on top row
            for (int i = left; i <= right; i++) {
                ans.add(matrix[top][i]);
            }
            top++;
            
            // 2. Traverse Top to Bottom on right column
            for (int i = top; i <= bottom; i++) {
                ans.add(matrix[i][right]);
            }
            right--;
            
            // 3. Traverse Right to Left on bottom row (if top row remains valid)
            if (top <= bottom) {
                for (int i = right; i >= left; i--) {
                    ans.add(matrix[bottom][i]);
                }
                bottom--;
            }
            
            // 4. Traverse Bottom to Top on left column (if left column remains valid)
            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    ans.add(matrix[i][left]);
                }
                left++;
            }
        }
        return ans;
    }
}
```
* **Time Complexity**: $O(M \times N)$
* **Space Complexity**: $O(1)$ auxiliary space (ignoring output list memory)

---

## 7️⃣ Dry Run
* Input: `[[1,2,3],[4,5,6],[7,8,9]]`
* Pointers: `top = 0, bottom = 2, left = 0, right = 2`
* `left to right (top = 0)`: `1, 2, 3` -> `top = 1`
* `top to bottom (right = 2)`: `6, 9` -> `right = 1`
* `right to left (bottom = 2)`: `8, 7` -> `bottom = 1`
* `bottom to top (left = 0)`: `4` -> `left = 1`
* Next iteration: `left to right (top = 1)`: `5` -> `top = 2` (breaks loop)
* Output: `[1,2,3,6,9,8,7,4,5]`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Forgetting the verification check `if (top <= bottom)` and `if (left <= right)` inside loop execution, which leads to duplicate printing of elements in rectangular matrices.

---

## 9️⃣ Key Takeaways
Boundary-shifting dynamically shrinks print space. Crucial approach for all grid-based traversal problems.

---

# 14. Count Subarrays with Given Sum

---

## 1️⃣ Problem Statement
Given an array of integers `nums` and an integer `k`, return the total number of subarrays whose sum equals to `k`.

---

## 2️⃣ What is Being Asked? — Simple Hinglish
Hume array ke andar aise total count of continuous subarrays find karne hain jinka sum target `k` ke barabar ho.

---

## 3️⃣ Example / Test Cases
| Input | Target | Output |
|---|---|---|
| `[1,1,1]` | 2 | `2` |
| `[1,2,3]` | 3 | `2` |

---

## 4️⃣ Constraints
* `1 <= nums.length <= 2 * 10^4`
* `-1000 <= nums[i] <= 1000`
* `-10^7 <= k <= 10^7`

---

## 5️⃣ C++ → Java Connection
C++: `unordered_map` count lookup. Java uses `HashMap` `getOrDefault()` to handle insertions cleanly.

C++:
```cpp
mpp[sum]++;
```
Java:
```java
map.put(sum, map.getOrDefault(sum, 0) + 1);
```

---

## 6️⃣ Solution Approaches

### Brute Force
Calculate sum of every possible subarray.
```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            int sum = 0;
            for (int j = i; j < n; j++) {
                sum += nums[j];
                if (sum == k) count++;
            }
        }
        return count;
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$

### Optimal (Prefix Sum + HashMap)
Keep track of running prefix sum. If `sum - k` is present in the map, add its frequency to our counter.
```java
import java.util.HashMap;

class Solution {
    public int subarraySum(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        // Base case: Prefix sum of 0 has seen 1 time initially
        map.put(0, 1);
        int sum = 0;
        int count = 0;
        
        for (int x : nums) {
            sum += x;
            int rem = sum - k;
            if (map.containsKey(rem)) {
                count += map.get(rem);
            }
            map.put(sum, map.getOrDefault(sum, 0) + 1);
        }
        return count;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$ (HashMap storage cost)

---

## 7️⃣ Dry Run
* Input: `[1, 1, 1]`, `k = 2`
* `map = {0: 1}`
* `x = 1`: `sum = 1`. `rem = 1 - 2 = -1` (no) -> `map = {0:1, 1:1}`
* `x = 1`: `sum = 2`. `rem = 2 - 2 = 0` (yes, freq = 1) -> `count = 1` -> `map = {0:1, 1:1, 2:1}`
* `x = 1`: `sum = 3`. `rem = 3 - 2 = 1` (yes, freq = 1) -> `count = 2` -> `map = {0:1, 1:1, 2:1, 3:1}`
* Output: `2`

---

## 8️⃣ Java-Specific Differences & Common Mistakes
Forgetting the base initialization `map.put(0, 1)`. If a subarray starting at index 0 has sum equal to `k`, `sum - k` will be 0. If `(0, 1)` is not in the map, this subarray will not be counted.

---

## 9️⃣ Key Takeaways
Prefix sum mapping resolves subarray count queries in linear time. Essential pattern for range-sum problems.

---

# 🎯 Final Striver Arrays Medium Checklist

- [ ] Two Sum
- [ ] Sort an array of 0's, 1's and 2's
- [ ] Majority Element-I
- [ ] Kadane's Algorithm — Maximum Subarray Sum
- [ ] Print Subarray with Maximum Subarray Sum
- [ ] Stock Buy and Sell
- [ ] Rearrange Array Elements by Sign
- [ ] Next Permutation
- [ ] Leaders in an Array
- [ ] Longest Consecutive Sequence in an Array
- [ ] Set Matrix Zeroes
- [ ] Rotate Matrix by 90 Degrees
- [ ] Print the Matrix in Spiral Manner
- [ ] Count Subarrays with Given Sum

---

# 🧠 Patterns Covered

- [ ] Hashing (HashMap)
- [ ] Two Pointer
- [ ] Dutch National Flag Algorithm
- [ ] Moore's Voting Algorithm
- [ ] Kadane's Algorithm (Dynamic Programming)
- [ ] Greedy Iteration
- [ ] Array Reversal Algorithm
- [ ] Prefix Sum Tracking
- [ ] Matrix Transpose and Swaps
- [ ] Grid Boundary Shifting
