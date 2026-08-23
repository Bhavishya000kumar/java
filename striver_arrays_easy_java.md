# Striver A2Z DSA — Arrays Easy in Java

## 🎯 Goal

This guide is designed for learners who already have a strong foundation in C++ and want to master **Arrays (Easy)** problems from Striver's A2Z DSA Sheet using **Java** for placements. 

- All solutions are implemented in **Java**.
- Key language differences between **C++** and **Java** are highlighted for every problem.
- Explanations are written in simple, beginner-friendly **Hinglish** to make logic tracing intuitive.
- The focus is on recognizing underlying **patterns** (e.g., Two Pointer, Sliding Window, Prefix Sum) rather than memorizing code templates.

---

## 📚 Complete Problem List

| # | Problem | Main Pattern | Difficulty |
|---|---|---|---|
| 1 | [Largest Element](#1-largest-element) | Array Traversal | Easy |
| 2 | [Second Largest Element](#2-second-largest-element) | Array Traversal | Easy |
| 3 | [Check if the Array is Sorted II](#3-check-if-the-array-is-sorted-ii) | Cyclic Checking | Easy |
| 4 | [Remove Duplicates from Sorted Array](#4-remove-duplicates-from-sorted-array) | Two Pointer | Easy |
| 5 | [Left Rotate Array by One](#5-left-rotate-array-by-one) | Shift Operation | Easy |
| 6 | [Left Rotate Array by K Places](#6-left-rotate-array-by-k-places) | Reversal Algorithm | Easy |
| 7 | [Move Zeroes to End](#7-move-zeroes-to-end) | Two Pointer | Easy |
| 8 | [Linear Search](#8-linear-search) | Array Traversal | Easy |
| 9 | [Union of Two Sorted Arrays](#9-union-of-two-sorted-arrays) | Two Pointer | Easy |
| 10 | [Find Missing Number](#10-find-missing-number) | Sum / XOR | Easy |
| 11 | [Maximum Consecutive Ones](#11-maximum-consecutive-ones) | Frequency Count | Easy |
| 12 | [Find the Number that Appears Once](#12-find-the-number-that-appears-once-and-other-numbers-twice) | XOR Bitwise | Easy |
| 13 | [Longest Subarray with Given Sum K (Positives)](#13-longest-subarray-with-given-sum-k-positives) | Sliding Window | Easy |
| 14 | [Longest Subarray with Sum K](#14-longest-subarray-with-sum-k-positives-negatives) | Prefix Sum + HashMap | Easy |

---

## 📌 Quick Navigation

- [1. Largest Element](#1-largest-element)
- [2. Second Largest Element](#2-second-largest-element)
- [3. Check if the Array is Sorted II](#3-check-if-the-array-is-sorted-ii)
- [4. Remove Duplicates from Sorted Array](#4-remove-duplicates-from-sorted-array)
- [5. Left Rotate Array by One](#5-left-rotate-array-by-one)
- [6. Left Rotate Array by K Places](#6-left-rotate-array-by-k-places)
- [7. Move Zeroes to End](#7-move-zeroes-to-end)
- [8. Linear Search](#8-linear-search)
- [9. Union of Two Sorted Arrays](#9-union-of-two-sorted-arrays)
- [10. Find Missing Number](#10-find-missing-number)
- [11. Maximum Consecutive Ones](#11-maximum-consecutive-ones)
- [12. Find the Number that Appears Once](#12-find-the-number-that-appears-once-and-other-numbers-twice)
- [13. Longest Subarray with Given Sum K (Positives)](#13-longest-subarray-with-given-sum-k-positives)
- [14. Longest Subarray with Sum K (Positives + Negatives)](#14-longest-subarray-with-sum-k-positives-negatives)

---

# 1. Largest Element

## 🔹 Problem Statement
Given an array `arr` of size `N`, find the largest element in the array.

## 🔹 What is Being Asked?
Basically humein array ke andar sabse bada (maximum) element find karna hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `arr = [3, 2, 1, 5, 2]` | `5` |
| `arr = [8, 10, 5, 7, 9]` | `10` |

## 🔹 Constraints
* `1 <= arr.length <= 10^5`
* `1 <= arr[i] <= 10^9`

## 🔹 C++ → Java Connection
* C++: `arr.size()`
* Java: `arr.length` (property, method nahi hai isliye parenthesis `()` nahi lagta).

### C++
```cpp
int n = arr.size();
int maxVal = arr[0];
```
### Java
```java
int n = arr.length;
int maxVal = arr[0];
```

## 🔹 Pattern / Concept
Array Traversal & Linear Scanning.

## 🔹 How to Think / Approach
Ek simple `max` variable lo jo pehle element `arr[0]` ko point kare. Uske baad poore array ko scan karte jao, aur agar koi element `max` se bada dikhe to `max` ko update kar do.

## 🔹 Brute Force Approach
Array ko sort kar do, aur end element return kar do.
```java
class Solution {
    public int largest(int[] arr) {
        java.util.Arrays.sort(arr);
        return arr[arr.length - 1];
    }
}
```
* **Time Complexity**: $O(N \log N)$ (sorting ki wajah se)
* **Space Complexity**: $O(1)$ (agar standard dual-pivot QuickSort use ho raha ho inline)

## 🔹 Optimal Approach
Single-pass linear traversal.
```java
class Solution {
    public int largest(int[] arr) {
        int max = arr[0];
        for (int i = 1; i < arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        return max;
    }
}
```
* **Time Complexity**: $O(N)$ (ek hi loop chalega)
* **Space Complexity**: $O(1)$ (no extra space)

## 🔹 Dry Run
* Input: `[3, 2, 1, 5, 2]`
* `max = 3`
* `i = 1`: `arr[1] = 2` -> `2 > 3` (false)
* `i = 2`: `arr[2] = 1` -> `1 > 3` (false)
* `i = 3`: `arr[3] = 5` -> `5 > 3` (true) -> `max = 5`
* `i = 4`: `arr[4] = 2` -> `2 > 5` (false)
* Result: `5`

## 🔹 Important Java Difference
Java primitive arrays have a static `.length` field. Do not use `.length()` or `.size()`.

## 🔹 Common Mistakes
Initializing `max` variable with `0` instead of `arr[0]` or `Integer.MIN_VALUE`. Agar array elements negative hue, to initial values errors introduce kar dengi.

## 🔹 Placement / Interview Point
A classic warmup problem in coding rounds. Ensure optimal $O(N)$ solution is written without sorting.

## 🔹 Related Problems
* Find the Smallest Element in an Array

## 🔹 Quick Revision
Scan through array once, maintain `max`, keep updating it. Time: $O(N)$, Space: $O(1)$.

---

# 2. Second Largest Element

## 🔹 Problem Statement
Given an array `arr` of size `N`, find the second largest distinct element in the array. If no such element exists (e.g., all elements are equal), return `-1`.

## 🔹 What is Being Asked?
Array mein se humein second largest element nikalna hai jo sabse bade element se chota ho aur distinct (alag) ho.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `arr = [12, 35, 1, 10, 34, 1]` | `34` |
| `arr = [10, 10, 10]` | `-1` |

## 🔹 Constraints
* `2 <= arr.length <= 10^5`
* `1 <= arr[i] <= 10^5`

## 🔹 C++ → Java Connection
Sorting comparisons: C++ uses `sort(arr.begin(), arr.end())`, Java uses `Arrays.sort(arr)`.

### C++
```cpp
sort(arr.begin(), arr.end());
```
### Java
```java
Arrays.sort(arr);
```

## 🔹 Pattern / Concept
Multi-variable tracking during single pass.

## 🔹 How to Think / Approach
Hum do tracking variables rakh sakte hain: `largest` aur `secondLargest`. Array ko update karte chalenge linear pass mein.

## 🔹 Brute Force Approach
Sort the array in ascending order. Loop from index `N-2` down to `0` and return the first element that is strictly less than the largest element `arr[N-1]`.
```java
class Solution {
    public int getSecondLargest(int[] arr) {
        java.util.Arrays.sort(arr);
        int n = arr.length;
        int largest = arr[n - 1];
        for (int i = n - 2; i >= 0; i--) {
            if (arr[i] != largest) {
                return arr[i];
            }
        }
        return -1;
    }
}
```
* **Time Complexity**: $O(N \log N)$ (sorting cost)
* **Space Complexity**: $O(1)$

## 🔹 Better Approach
Two passes.
1. Find the largest element.
2. Traverse array again, find the largest element which is strictly less than the largest element.
```java
class Solution {
    public int getSecondLargest(int[] arr) {
        int largest = -1;
        for (int x : arr) {
            if (x > largest) largest = x;
        }
        int secondLargest = -1;
        for (int x : arr) {
            if (x > secondLargest && x < largest) {
                secondLargest = x;
            }
        }
        return secondLargest;
    }
}
```
* **Time Complexity**: $O(N + N) = O(N)$ (two linear passes)
* **Space Complexity**: $O(1)$

## 🔹 Optimal Approach
Single pass traversal updating both `largest` and `secondLargest`.
```java
class Solution {
    public int getSecondLargest(int[] arr) {
        int largest = -1;
        int secondLargest = -1;
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] > largest) {
                secondLargest = largest;
                largest = arr[i];
            } else if (arr[i] < largest && arr[i] > secondLargest) {
                secondLargest = arr[i];
            }
        }
        return secondLargest;
    }
}
```
* **Time Complexity**: $O(N)$ (single pass)
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
Input: `[12, 35, 1, 10, 34, 1]`
* `largest = -1`, `secondLargest = -1`
* `i = 0 (12)`: `12 > -1` -> `secondLargest = -1`, `largest = 12`
* `i = 1 (35)`: `35 > 12` -> `secondLargest = 12`, `largest = 35`
* `i = 2 (1)`: `1 > 35` (false), `1 < 35 && 1 > 12` (false)
* `i = 3 (10)`: `10 > 35` (false), `10 < 35 && 10 > 12` (false)
* `i = 4 (34)`: `34 > 35` (false), `34 < 35 && 34 > 12` (true) -> `secondLargest = 34`
* `i = 5 (1)`: No change.
* Result: `34`

## 🔹 Important Java Difference
Java variables must be initialized before read. Setting them to `-1` aligns with requirements (as `arr[i] >= 1` according to constraints).

## 🔹 Common Mistakes
* Not checking for duplicate largest elements.
* Returning array index instead of value.

## 🔹 Placement / Interview Point
Frequent question in screening rounds. Expectation is always $O(N)$ time with $O(1)$ space using a single pass.

## 🔹 Related Problems
* Find the Second Smallest Element in an Array.

## 🔹 Quick Revision
Maintain `largest` and `secondLargest`. If a new element is larger than `largest`, shift the values. Else if it lies between `largest` and `secondLargest`, update `secondLargest`.

---

# 3. Check if the Array is Sorted II

## 🔹 Problem Statement
Given an array `nums`, return `true` if the array was originally sorted in non-decreasing order, then rotated some number of positions (including zero). Otherwise, return `false`.

## 🔹 What is Being Asked?
Humein yeh check karna hai ki kya array originally sorted tha aur fir usko cyclic rotate kiya gaya. Agar check karenge cyclic manner mein, to boundary rules ko include karke pure array mein at most ek hi violation (`nums[i] > nums[i+1]`) hona chahiye.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `nums = [3, 4, 5, 1, 2]` | `true` |
| `nums = [2, 1, 3, 4]` | `false` |

## 🔹 Constraints
* `1 <= nums.length <= 100`
* `1 <= nums[i] <= 100`

## 🔹 C++ → Java Connection
Modulo logic remains identical. We use `nums.length` in Java.

### C++
```cpp
int n = nums.size();
```
### Java
```java
int n = nums.length;
```

## 🔹 Pattern / Concept
Cyclic comparison using modulo arithmetic.

## 🔹 How to Think / Approach
Agar ek sorted array rotate hota hai, to usme violations count `nums[i] > nums[(i + 1) % n]` check karne par pure cyclic space mein maximum **ek** hi violation milegi. Agar violation count `0` ya `1` hai, to return true, else false.

## 🔹 Optimal Approach
Single-pass violation count checking. Simple approach is optimal here.
```java
class Solution {
    public boolean check(int[] nums) {
        int count = 0;
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            if (nums[i] > nums[(i + 1) % n]) {
                count++;
            }
        }
        return count <= 1;
    }
}
```
* **Time Complexity**: $O(N)$ (iterates exactly once)
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
Input: `nums = [3, 4, 5, 1, 2]`
* `i = 0`: `nums[0] (3) > nums[1] (4)` (false)
* `i = 1`: `nums[1] (4) > nums[2] (5)` (false)
* `i = 2`: `nums[2] (5) > nums[3] (1)` (true) -> `count = 1`
* `i = 3`: `nums[3] (1) > nums[4] (2)` (false)
* `i = 4`: `nums[4] (2) > nums[0] (3)` (false)
* Final `count = 1` -> returns `true`.

## 🔹 Important Java Difference
No specific structural differences except index bounds verification. Modulo `% n` ensures no `ArrayIndexOutOfBoundsException`.

## 🔹 Common Mistakes
Forgetting to check the wrap-around condition (`nums[n-1] > nums[0]`).

## 🔹 Placement / Interview Point
LeetCode 1752. Interviewers look for clean code using modulo rather than checking rotated state by creating subarrays.

## 🔹 Related Problems
* Check if Array is Sorted and Rotated.

## 🔹 Quick Revision
Count cyclic drop points: `nums[i] > nums[(i+1)%n]`. If count <= 1, return true.

---

# 4. Remove Duplicates from Sorted Array

## 🔹 Problem Statement
Given a sorted array `nums`, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same. Return the count of unique elements.

## 🔹 What is Being Asked?
Sorted array mein se duplicates hatane hain aur original array ko modify karke starting mein saare unique elements lane hain. Final unique list ki length return karni hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `nums = [1, 1, 2]` | `2, nums = [1, 2, _]` |
| `nums = [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]` | `5, nums = [0, 1, 2, 3, 4, _, _, _, _, _]` |

## 🔹 Constraints
* `1 <= nums.length <= 3 * 10^4`
* `-100 <= nums[i] <= 100`

## 🔹 C++ → Java Connection
* C++: `std::set`
* Java: `HashSet` / `LinkedHashSet` (duplicate elimination).

### C++
```cpp
set<int> st;
```
### Java
```java
HashSet<Integer> st = new HashSet<>();
```

## 🔹 Pattern / Concept
Two-pointer technique.

## 🔹 How to Think / Approach
Kyunki array sorted hai, hum do pointers `i` aur `j` le sakte hain. Pointer `i` hamesha index point karega latest unique element ka. Pointer `j` poore array ko cross karega. Jab `nums[j] != nums[i]` hoga, tab unique pointer increment karke use updates denge.

## 🔹 Brute Force Approach
Use a `LinkedHashSet` to collect unique elements in order, then write them back to the array.
```java
import java.util.*;

class Solution {
    public int removeDuplicates(int[] nums) {
        LinkedHashSet<Integer> set = new LinkedHashSet<>();
        for (int x : nums) {
            set.add(x);
        }
        int index = 0;
        for (int x : set) {
            nums[index++] = x;
        }
        return set.size();
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$ (temp hash set memory)

## 🔹 Optimal Approach
Two-pointer in-place solution.
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;
        int i = 0;
        for (int j = 1; j < nums.length; j++) {
            if (nums[j] != nums[i]) {
                i++;
                nums[i] = nums[j];
            }
        }
        return i + 1;
    }
}
```
* **Time Complexity**: $O(N)$ (single scan)
* **Space Complexity**: $O(1)$ (no extra space utilized)

## 🔹 Dry Run
Input: `nums = [1, 1, 2]`
* `i = 0`, `j = 1`: `nums[1] (1) == nums[0] (1)` -> loop continues
* `i = 0`, `j = 2`: `nums[2] (2) != nums[0] (1)` -> `i++` (1), `nums[1] = nums[2] (2)`
* Return `i + 1 = 2`. Modified prefix: `[1, 2]`.

## 🔹 Important Java Difference
LinkedHashSet keeps the insertion order, unlike normal HashSet which is unordered. For sorted structures, order retention is critical if sets are used.

## 🔹 Common Mistakes
* Iterating from index 0 instead of 1 for the second pointer.
* Returning pointer index `i` instead of count `i + 1`.

## 🔹 Placement / Interview Point
Classic Two-pointer interview pattern. Standard expectation is $O(1)$ space.

## 🔹 Related Problems
* Remove Element (LeetCode 27).

## 🔹 Quick Revision
Keep pointer `i = 0`. Iterate `j` from 1 to end. If different element found, increment `i`, copy `nums[j]` to `nums[i]`. Return `i + 1`.

---

# 5. Left Rotate Array by One

## 🔹 Problem Statement
Given an array `arr` of size `N`, left rotate the array by one position.

## 🔹 What is Being Asked?
Array ke saare elements ko ek place left shifting karni hai aur pehle element ko khinch ke last position par dalna hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `arr = [1, 2, 3, 4, 5]` | `[2, 3, 4, 5, 1]` |

## 🔹 Constraints
* `1 <= arr.length <= 10^5`

## 🔹 C++ → Java Connection
Standard shifts. No collection mapping necessary.

### C++
```cpp
int temp = arr[0];
```
### Java
```java
int temp = arr[0];
```

## 🔹 Pattern / Concept
Array shifting operations.

## 🔹 How to Think / Approach
Pehle element ko store karke save kar lo. Uske baad bache hue saare values ko copy kar do: `arr[i-1] = arr[i]`. End position `N-1` par save kiya hua temp element copy kar do.

## 🔹 Optimal Approach
Simple array shifting.
```java
class Solution {
    public void rotateByOne(int[] arr) {
        int n = arr.length;
        if (n <= 1) return;
        int temp = arr[0];
        for (int i = 1; i < n; i++) {
            arr[i - 1] = arr[i];
        }
        arr[n - 1] = temp;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
Input: `[1, 2, 3, 4, 5]`
* `temp = 1`
* `i = 1`: `arr[0] = arr[1]` -> array: `[2, 2, 3, 4, 5]`
* `i = 2`: `arr[1] = arr[2]` -> array: `[2, 3, 3, 4, 5]`
* `i = 3`: `arr[2] = arr[3]` -> array: `[2, 3, 4, 4, 5]`
* `i = 4`: `arr[3] = arr[4]` -> array: `[2, 3, 4, 5, 5]`
* End assign: `arr[4] = temp (1)` -> final: `[2, 3, 4, 5, 1]`

## 🔹 Important Java Difference
Java array elements shift manually, as there's no native rotate function for primitive arrays.

## 🔹 Common Mistakes
* Overwriting elements before saving `arr[0]`.
* Off-by-one errors in index boundaries.

## 🔹 Placement / Interview Point
Simple shifting concept. Frequently asked to check clean index loop constraints handling.

## 🔹 Related Problems
* Right Rotate Array by One.

## 🔹 Quick Revision
Save first element, shift rest of the elements left, put first element at the end. Time: $O(N)$, Space: $O(1)$.

---

# 6. Left Rotate Array by K Places

## 🔹 Problem Statement
Given an array `arr` of size `N`, rotate the array to the left by `K` steps, where `K` is non-negative.

## 🔹 What is Being Asked?
Array ke elements ko `K` places circular left shift karna hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `arr = [1, 2, 3, 4, 5, 6, 7], k = 3` | `[4, 5, 6, 7, 1, 2, 3]` |

## 🔹 Constraints
* `1 <= arr.length <= 10^5`
* `0 <= k <= 10^5`

## 🔹 C++ → Java Connection
We can write a generic `reverse()` helper method in Java since it is built-in inside `<algorithm>` in C++ via `reverse(first, last)`.

### C++
```cpp
reverse(arr.begin(), arr.begin() + k);
```
### Java
```java
reverse(arr, 0, k - 1);
```

## 🔹 Pattern / Concept
Reversal Algorithm (Space Optimization).

## 🔹 How to Think / Approach
`K` index ranges verify karne ke baad, pure swap optimization ko 3 reverse operations se kar sakte hain:
1. Reverse first `K` elements.
2. Reverse remaining `N - K` elements.
3. Reverse complete array.

## 🔹 Brute Force Approach
Create a temporary array of size `K`, copy first `K` elements to temp, shift remaining elements left, copy temp back to the end of array.
```java
class Solution {
    public void rotate(int[] arr, int k) {
        int n = arr.length;
        k = k % n;
        int[] temp = new int[k];
        for (int i = 0; i < k; i++) {
            temp[i] = arr[i];
        }
        for (int i = k; i < n; i++) {
            arr[i - k] = arr[i];
        }
        for (int i = 0; i < k; i++) {
            arr[n - k + i] = temp[i];
        }
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(K)$

## 🔹 Optimal Approach
Reversal algorithm in-place.
```java
class Solution {
    public void rotate(int[] arr, int k) {
        int n = arr.length;
        k = k % n;
        reverse(arr, 0, k - 1);
        reverse(arr, k, n - 1);
        reverse(arr, 0, n - 1);
    }
    
    private void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
}
```
* **Time Complexity**: $O(N)$ (each element reversed twice at max)
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
Input: `[1, 2, 3, 4, 5, 6, 7], k = 3`
* Step 1: reverse `0` to `2` -> `[3, 2, 1, 4, 5, 6, 7]`
* Step 2: reverse `3` to `6` -> `[3, 2, 1, 7, 6, 5, 4]`
* Step 3: reverse `0` to `6` -> `[4, 5, 6, 7, 1, 2, 3]`
* Done.

## 🔹 Important Java Difference
Custom helper methods like `reverse()` are highly useful because Java `Arrays` utility does not have an in-place primitive reverse.

## 🔹 Common Mistakes
* Not checking `k = k % n`. If `k` is larger than `n`, it can throw index exceptions.
* Reversing the wrong index pairs.

## 🔹 Placement / Interview Point
Important question for optimization testing. Always write the Reversal algorithm to get top ratings in rounds.

## 🔹 Related Problems
* Right Rotate Array by K Places.

## 🔹 Quick Revision
Mod `k` with size. Reverse `0` to `k-1`, reverse `k` to `n-1`, reverse entire array.

---

# 7. Move Zeroes to End

## 🔹 Problem Statement
Given an array `nums`, move all `0`s to the end of it while maintaining the relative order of the non-zero elements.

## 🔹 What is Being Asked?
Array ke saare zeroes ko end mein transfer karna hai bina bache hue positive/negative numbers ka order bigade.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `nums = [0, 1, 0, 3, 12]` | `[1, 3, 12, 0, 0]` |

## 🔹 Constraints
* `1 <= nums.length <= 10^4`

## 🔹 C++ → Java Connection
Manual implementation vs STL features.

### C++
```cpp
std::stable_partition(nums.begin(), nums.end(), [](int n) { return n != 0; });
```
### Java
```java
// Manual index pointer manipulation
```

## 🔹 Pattern / Concept
Two-pointer partitioning.

## 🔹 How to Think / Approach
Ek target pointer `j` trace karega first zero element ki position. Loop execute karte hue hum aage ke elements check karenge, aur jab non-zero element dikhega use swap kar denge `j` position par.

## 🔹 Brute Force Approach
Copy all non-zero elements to a temporary list, fill the rest with zeroes.
```java
import java.util.ArrayList;

class Solution {
    public void moveZeroes(int[] nums) {
        ArrayList<Integer> temp = new ArrayList<>();
        for (int x : nums) {
            if (x != 0) temp.add(x);
        }
        for (int i = 0; i < temp.size(); i++) {
            nums[i] = temp.get(i);
        }
        for (int i = temp.size(); i < nums.length; i++) {
            nums[i] = 0;
        }
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$

## 🔹 Optimal Approach
Two-pointer swap mechanism in-place.
```java
class Solution {
    public void moveZeroes(int[] nums) {
        int n = nums.length;
        int j = -1;
        // Step 1: Find the first zero index
        for (int i = 0; i < n; i++) {
            if (nums[i] == 0) {
                j = i;
                break;
            }
        }
        // If there are no zeroes, we do not need to do anything
        if (j == -1) return;
        
        // Step 2: Swap non-zero elements with the zero index
        for (int i = j + 1; i < n; i++) {
            if (nums[i] != 0) {
                // swap
                int temp = nums[i];
                nums[i] = nums[j];
                nums[j] = temp;
                j++;
            }
        }
    }
}
```
* **Time Complexity**: $O(N)$ (exactly one linear traversal scan)
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
Input: `nums = [0, 1, 0, 3, 12]`
* `j` finds zero at index `0` -> `j = 0`
* Loop starts at `i = 1`: `nums[1] = 1 != 0` -> swap index `1` and `0` -> array: `[1, 0, 0, 3, 12]`, `j` becomes `1`
* `i = 2`: `nums[2] = 0` (no change)
* `i = 3`: `nums[3] = 3 != 0` -> swap index `3` and `1` -> array: `[1, 3, 0, 0, 12]`, `j` becomes `2`
* `i = 4`: `nums[4] = 12 != 0` -> swap index `4` and `2` -> array: `[1, 3, 12, 0, 0]`, `j` becomes `3`
* Loop completes. Result: `[1, 3, 12, 0, 0]`

## 🔹 Important Java Difference
No default partition structure available in Java primitive arrays. Manual swaps are straightforward and fast.

## 🔹 Common Mistakes
* Losing the track index of the first zero.
* Messing up relative order of values during swap operations.

## 🔹 Placement / Interview Point
Frequent test problem on array manipulation. In-place optimal solution is standard requirement.

## 🔹 Related Problems
* Move Negative Numbers to End.

## 🔹 Quick Revision
Find first zero index `j`. Loop `i` from `j + 1` to end. Swap non-zero elements at `i` with `j` and increment `j`.

---

# 8. Linear Search

## 🔹 Problem Statement
Given an array `arr` and a target element `K`, search for `K` in the array. Return its 0-based index if found, else return `-1`.

## 🔹 What is Being Asked?
Array mein sequential check karke target element `K` ko find karna hai. Agar mil jaye to index return karo, nahi to `-1`.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `arr = [1, 2, 3, 4, 5], k = 4` | `3` |
| `arr = [1, 2, 3, 4, 5], k = 6` | `-1` |

## 🔹 Constraints
* `1 <= arr.length <= 10^5`

## 🔹 C++ → Java Connection
`std::find` in C++ returns an iterator. In Java, search loops are written manually.

### C++
```cpp
auto it = find(arr.begin(), arr.end(), k);
```
### Java
```java
// Manual linear loop traversal
```

## 🔹 Pattern / Concept
Sequential Scanning.

## 🔹 How to Think / Approach
Array ko starting from index 0 se end tak check karo. Agar target element target coordinate match kar jata hai, to current loop state check index return kar do.

## 🔹 Optimal Approach
Simple approach hi optimal hai.
```java
class Solution {
    public int searchInArray(int[] arr, int k) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == k) {
                return i;
            }
        }
        return -1;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
* Input: `[1, 2, 3, 4, 5]`, `k = 4`
* `i = 0`: `arr[0] = 1 != 4`
* `i = 1`: `arr[1] = 2 != 4`
* `i = 2`: `arr[2] = 3 != 4`
* `i = 3`: `arr[3] = 4 == 4` -> returns `3`.

## 🔹 Important Java Difference
Java traversal requires accessing elements directly using brackets `arr[i]`.

## 🔹 Common Mistakes
* Returning value instead of index.
* Off-by-one loop conditions.

## 🔹 Placement / Interview Point
Simple testing logic. Usually serves as a building block for complex searching algorithms.

## 🔹 Related Problems
* Binary Search.

## 🔹 Quick Revision
Loop from start to end, match values, return matching index or `-1`.

---

# 9. Union of Two Sorted Arrays

## 🔹 Problem Statement
Given two sorted arrays `arr1` and `arr2`, return their union as a sorted list containing unique elements.

## 🔹 What is Being Asked?
Do sorted arrays ka union (saare unique elements ascending order mein) dynamic array structure list ke format mein return karna hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `arr1 = [1, 2, 3, 4, 5]`, `arr2 = [1, 2, 3, 6, 7]` | `[1, 2, 3, 4, 5, 6, 7]` |

## 🔹 Constraints
* `1 <= arr1.length, arr2.length <= 10^5`

## 🔹 C++ → Java Connection
* C++: `std::set`
* Java: `TreeSet` (preserves sorted nature and uniqueness).
* C++: `std::set_union`
* Java: Two-pointers logic returning `ArrayList<Integer>`.

### C++
```cpp
set<int> st;
```
### Java
```java
TreeSet<Integer> st = new TreeSet<>();
```

## 🔹 Pattern / Concept
Two-pointer merge operation.

## 🔹 How to Think / Approach
Kyunki dono arrays sorted hain, hum merge sort style pointers `i` and `j` allocate karenge. Elements ko compare karte hue result array list mein insert karenge, ensure karenge ki duplicates list ke end checks mein overlap na ho.

## 🔹 Brute Force Approach
Insert all elements of both arrays into a `TreeSet` to keep them sorted and unique, then copy to list.
```java
import java.util.*;

class Solution {
    public ArrayList<Integer> findUnion(int[] arr1, int[] arr2) {
        TreeSet<Integer> set = new TreeSet<>();
        for (int x : arr1) set.add(x);
        for (int x : arr2) set.add(x);
        return new ArrayList<>(set);
    }
}
```
* **Time Complexity**: $O((N + M) \log(N + M))$
* **Space Complexity**: $O(N + M)$

## 🔹 Optimal Approach
Two-pointer algorithm to merge unique elements directly.
```java
import java.util.ArrayList;

class Solution {
    public ArrayList<Integer> findUnion(int[] arr1, int[] arr2) {
        int n1 = arr1.length;
        int n2 = arr2.length;
        int i = 0, j = 0;
        ArrayList<Integer> union = new ArrayList<>();
        
        while (i < n1 && j < n2) {
            if (arr1[i] <= arr2[j]) {
                if (union.isEmpty() || union.get(union.size() - 1) != arr1[i]) {
                    union.add(arr1[i]);
                }
                i++;
            } else {
                if (union.isEmpty() || union.get(union.size() - 1) != arr2[j]) {
                    union.add(arr2[j]);
                }
                j++;
            }
        }
        
        while (i < n1) {
            if (union.isEmpty() || union.get(union.size() - 1) != arr1[i]) {
                union.add(arr1[i]);
            }
            i++;
        }
        
        while (j < n2) {
            if (union.isEmpty() || union.get(union.size() - 1) != arr2[j]) {
                union.add(arr2[j]);
                }
            j++;
        }
        
        return union;
    }
}
```
* **Time Complexity**: $O(N + M)$
* **Space Complexity**: $O(1)$ auxiliary space (ignoring output `ArrayList` memory)

## 🔹 Dry Run
Input: `arr1 = [1, 2, 3]`, `arr2 = [2, 3, 4]`
* `i = 0`, `j = 0`: `arr1[0] = 1 < arr2[0] = 2` -> `union = [1]`, `i = 1`
* `i = 1`, `j = 0`: `arr1[1] = 2 == arr2[0] = 2` -> `union = [1, 2]`, `i = 2`
* `i = 2`, `j = 0`: `arr1[2] = 3 > arr2[0] = 2` -> `union.get(1) = 2 == 2` -> increment `j` to `1`
* `i = 2`, `j = 1`: `arr1[2] = 3 == arr2[1] = 3` -> `union = [1, 2, 3]`, `i = 3`
* `i` finishes. Loop continues for `j < n2` (index 2: value 4) -> `union = [1, 2, 3, 4]`, `j = 3`
* Result: `[1, 2, 3, 4]`.

## 🔹 Important Java Difference
In Java, `union.get(union.size() - 1)` helps to access the last element of the list, which serves as our duplication filter check.

## 🔹 Common Mistakes
* Not checking for `union.isEmpty()` before calling `union.get()`.
* Missing duplicate validations on secondary arrays extraction loops.

## 🔹 Placement / Interview Point
Frequent question tested in core companies. Focus is on $O(N+M)$ merging logic rather than simple sorting.

## 🔹 Related Problems
* Intersection of Two Sorted Arrays.

## 🔹 Quick Revision
Pointers `i` and `j`. Add smaller to union list if not equal to the last added element. Iterate until both arrays finish.

---

# 10. Find Missing Number

## 🔹 Problem Statement
Given an array containing `N` distinct numbers in the range `[0, N]`, return the only number in the range that is missing.

## 🔹 What is Being Asked?
Humein 0 se `N` range ke numbers ka array diya gaya hai, jisme se ek number missing hai. Use trace karke return karna hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `nums = [3, 0, 1]` | `2` |
| `nums = [9, 6, 4, 2, 3, 5, 7, 0, 1]` | `8` |

## 🔹 Constraints
* `n == nums.length`
* `1 <= n <= 10^4`
* `0 <= nums[i] <= n`

## 🔹 C++ → Java Connection
Logic is identical. Sum operations use simple scalar variables.

### C++
```cpp
int expectedSum = n * (n + 1) / 2;
```
### Java
```java
int expectedSum = n * (n + 1) / 2;
```

## 🔹 Pattern / Concept
Sum formula / Bitwise XOR cancellation.

## 🔹 How to Think / Approach
Maths approach: `Sum of 1 to N` ka calculation simple hai. Array ke items ka sum subtract kar denge expected sum se. Alternatively, XOR cancellation technique use kar sakte hain jo range elements aur array elements ko overlap karke missing value nikalta hai (XOR technique standard overflows prevent karti hai).

## 🔹 Brute Force Approach
Linear search for each number in the range `[0, N]` inside the array.
```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        for (int i = 0; i <= n; i++) {
            boolean found = false;
            for (int x : nums) {
                if (x == i) {
                    found = true;
                    break;
                }
            }
            if (!found) return i;
        }
        return -1;
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$

## 🔹 Better Approach
Use a boolean hash array of size `N + 1` to track occurrence states of each element.
```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        boolean[] exists = new boolean[n + 1];
        for (int x : nums) {
            exists[x] = true;
        }
        for (int i = 0; i <= n; i++) {
            if (!exists[i]) return i;
        }
        return -1;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$

## 🔹 Optimal Approach
Bitwise XOR cancelation logic.
```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int xorVal = 0;
        // XOR all numbers in range [1, N]
        for (int i = 1; i <= n; i++) {
            xorVal ^= i;
        }
        // XOR all array elements
        for (int x : nums) {
            xorVal ^= x;
        }
        return xorVal;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
Input: `nums = [3, 0, 1]`
* `n = 3`
* `xorVal = 0`
* XOR range `[1, 3]`: `xorVal = 0 ^ 1 ^ 2 ^ 3`
* XOR array: `(0 ^ 1 ^ 2 ^ 3) ^ (3 ^ 0 ^ 1) = (1 ^ 1) ^ (3 ^ 3) ^ (0 ^ 0) ^ 2 = 0 ^ 0 ^ 0 ^ 2 = 2`
* Return: `2`

## 🔹 Important Java Difference
No explicit differences. Standard bitwise operators (`^`) behave similarly in C++ and Java.

## 🔹 Common Mistakes
Sum formulas can cause integer overflow if $N$ is very large (e.g. $> 10^5$ and output is stored in standard `int`). Use XOR approach as it is safer and preferred.

## 🔹 Placement / Interview Point
Standard logic testing. XOR solution showcases deep system optimization understanding.

## 🔹 Related Problems
* Single Number (LeetCode 136).

## 🔹 Quick Revision
XOR all range indices `[1, N]` with all elements of the array. The resultant value is the missing number.

---

# 11. Maximum Consecutive Ones

## 🔹 Problem Statement
Given a binary array `nums`, return the maximum number of consecutive `1`s in the array.

## 🔹 What is Being Asked?
Humein array ke andar lagatar (continuous) aane wale `1`s ki max count return karni hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `nums = [1, 1, 0, 1, 1, 1]` | `3` |

## 🔹 Constraints
* `1 <= nums.length <= 10^5`
* `nums[i]` is either `0` or `1`.

## 🔹 C++ → Java Connection
Standard traversal constructs.

### C++
```cpp
maxCount = max(maxCount, count);
```
### Java
```java
maxCount = Math.max(maxCount, count);
```

## 🔹 Pattern / Concept
Running counters tracking.

## 🔹 How to Think / Approach
Array traversal karte jao. Agar current element `1` hai, increment `count` variable. Uske baad `max` values update kar do. Agar `0` dikhe, to counts ko reset kar do (`count = 0`).

## 🔹 Optimal Approach
Simple approach hi optimal hai.
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int max = 0;
        int count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 1) {
                count++;
                max = Math.max(max, count);
            } else {
                count = 0;
            }
        }
        return max;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
Input: `[1, 1, 0, 1, 1, 1]`
* `i = 0`: `nums[0] = 1` -> `count = 1`, `max = 1`
* `i = 1`: `nums[1] = 1` -> `count = 2`, `max = 2`
* `i = 2`: `nums[2] = 0` -> `count = 0`
* `i = 3`: `nums[3] = 1` -> `count = 1`, `max = 2`
* `i = 4`: `nums[4] = 1` -> `count = 2`, `max = 2`
* `i = 5`: `nums[5] = 1` -> `count = 3`, `max = 3`
* Return: `3`

## 🔹 Important Java Difference
Use `Math.max()` for maximum updates instead of manual `if` branches for cleaner style.

## 🔹 Common Mistakes
Resetting count but forgetting to capture the max count before resetting.

## 🔹 Placement / Interview Point
Frequently asked in startup rounds as a basic sliding window precursor.

## 🔹 Related Problems
* Max Consecutive Ones II (flipping at most one zero).

## 🔹 Quick Revision
Keep current count and global max. Loop: increment count on `1` and update max; reset count on `0`.

---

# 12. Find the Number that Appears Once, and Other Numbers Twice

## 🔹 Problem Statement
Given a non-empty array of integers `nums`, every element appears twice except for one. Find that single one.

## 🔹 What is Being Asked?
Array mein lagbhag saare elements double aate hain, par ek element akele (single time) aata hai. Us unique element ko trace karna hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `nums = [2, 2, 1]` | `1` |
| `nums = [4, 1, 2, 1, 2]` | `4` |

## 🔹 Constraints
* `1 <= nums.length <= 3 * 10^4`
* `-3 * 10^4 <= nums[i] <= 3 * 10^4`

## 🔹 C++ → Java Connection
* C++: `unordered_map<int, int>`
* Java: `HashMap<Integer, Integer>` (storing frequencies).

### C++
```cpp
unordered_map<int, int> mpp;
```
### Java
```java
HashMap<Integer, Integer> mpp = new HashMap<>();
```

## 🔹 Pattern / Concept
Bitwise XOR cancellation properties.

## 🔹 How to Think / Approach
XOR operator property check:
* $A \oplus A = 0$ (Self-XOR cancel matching numbers)
* $A \oplus 0 = A$ (XOR with zero returns itself)
Array ke saare elements ka continuous XOR le lo. Saare double appearance variables cut out hokar `0` ban jayenge aur final single element remain karega.

## 🔹 Brute Force Approach
Linear search nested checks, counting occurrences of each element.
```java
class Solution {
    public int singleNumber(int[] nums) {
        for (int i = 0; i < nums.length; i++) {
            int count = 0;
            for (int j = 0; j < nums.length; j++) {
                if (nums[i] == nums[j]) count++;
            }
            if (count == 1) return nums[i];
        }
        return -1;
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$

## 🔹 Better Approach
Use a hash map to save frequency states of each element.
```java
import java.util.HashMap;

class Solution {
    public int singleNumber(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int x : nums) {
            map.put(x, map.getOrDefault(x, 0) + 1);
        }
        for (int x : nums) {
            if (map.get(x) == 1) return x;
        }
        return -1;
    }
}
```
* **Time Complexity**: $O(N)$
* **Space Complexity**: $O(N)$

## 🔹 Optimal Approach
Bitwise XOR.
```java
class Solution {
    public int singleNumber(int[] nums) {
        int xor = 0;
        for (int x : nums) {
            xor ^= x;
        }
        return xor;
    }
}
```
* **Time Complexity**: $O(N)$ (single pass)
* **Space Complexity**: $O(1)$ (no extra space)

## 🔹 Dry Run
Input: `nums = [4, 1, 2, 1, 2]`
* `xor = 4 ^ 1 ^ 2 ^ 1 ^ 2`
* Re-ordering: `4 ^ (1 ^ 1) ^ (2 ^ 2) = 4 ^ 0 ^ 0 = 4`
* Output: `4`

## 🔹 Important Java Difference
In Java collections, use wrapper class `Integer` instead of `int`. `map.getOrDefault(key, default)` checks exist state cleanly.

## 🔹 Common Mistakes
Initializing `xor` variable with something else instead of `0`.

## 🔹 Placement / Interview Point
LeetCode 136. Very common placement logic problem. Expectation is always $O(N)$ time and $O(1)$ space.

## 🔹 Related Problems
* Single Number II / III.

## 🔹 Quick Revision
XOR all elements in the array. Duplicates cancel out, leaving the unique element.

---

# 13. Longest Subarray with Given Sum K (Positives)

## 🔹 Problem Statement
Given an array `arr` of size `N` containing only positive integers and an integer `K`, find the length of the longest subarray with a sum equal to `K`.

## 🔹 What is Being Asked?
Array mein humein check karna hai ki sum equal to `K` banane wala longest continuous subarray kaunsa hai. Note: array mein sirf positive elements aur `0` ho sakte hain.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `arr = [10, 5, 2, 7, 1, 9]`, `k = 15` | `4` (Subarray `[5, 2, 7, 1]`) |
| `arr = [1, 2, 3]`, `k = 3` | `2` (Subarray `[1, 2]`) |

## 🔹 Constraints
* `1 <= arr.length <= 10^5`
* `0 <= arr[i] <= 10^9`
* `1 <= k <= 10^9`

## 🔹 C++ → Java Connection
Two-pointer sliding window variables logic.

### C++
```cpp
int left = 0, right = 0;
```
### Java
```java
int left = 0, right = 0;
```

## 🔹 Pattern / Concept
Sliding Window & Two Pointer.

## 🔹 How to Think / Approach
Pointers `left` and `right` sliding window control karenge. Element values add karte chalenge, aur jab `sum > K` ho jaye, pointer `left` shift karke left values remove karte jayenge jab tak `sum <= K` na ho jaye.

## 🔹 Brute Force Approach
Generate all subarrays, calculate their sums, and find the maximum length of subarray with sum `K`.
```java
class Solution {
    public int longestSubarray(int[] arr, int k) {
        int maxLen = 0;
        int n = arr.length;
        for (int i = 0; i < n; i++) {
            long sum = 0;
            for (int j = i; j < n; j++) {
                sum += arr[j];
                if (sum == k) {
                    maxLen = Math.max(maxLen, j - i + 1);
                }
            }
        }
        return maxLen;
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$

## 🔹 Better Approach
Prefix Sum using HashMap.
```java
import java.util.HashMap;

class Solution {
    public int longestSubarray(int[] arr, int k) {
        HashMap<Long, Integer> map = new HashMap<>();
        long sum = 0;
        int maxLen = 0;
        for (int i = 0; i < arr.length; i++) {
            sum += arr[i];
            if (sum == k) {
                maxLen = i + 1;
            }
            if (map.containsKey(sum - k)) {
                maxLen = Math.max(maxLen, i - map.get(sum - k));
            }
            if (!map.containsKey(sum)) {
                map.put(sum, i);
            }
        }
        return maxLen;
    }
}
```
* **Time Complexity**: $O(N)$ (average case using HashMap)
* **Space Complexity**: $O(N)$ (storing prefix sums)

## 🔹 Optimal Approach
Two-pointer / Sliding window.
```java
class Solution {
    public int longestSubarray(int[] arr, int k) {
        int left = 0;
        int right = 0;
        long sum = 0;
        int maxLen = 0;
        int n = arr.length;
        
        while (right < n) {
            sum += arr[right];
            
            // Shrink window if sum exceeds k
            while (left <= right && sum > k) {
                sum -= arr[left];
                left++;
            }
            
            if (sum == k) {
                maxLen = Math.max(maxLen, right - left + 1);
            }
            right++;
        }
        return maxLen;
    }
}
```
* **Time Complexity**: $O(N)$ (each pointer moves at most $N$ times)
* **Space Complexity**: $O(1)$

## 🔹 Dry Run
Input: `arr = [10, 5, 2, 7, 1]`, `k = 15`
* `right = 0`: `sum = 10` -> `maxLen = 0`
* `right = 1`: `sum = 15` -> `maxLen = 2` (Subarray: `[10, 5]`)
* `right = 2`: `sum = 17` -> `sum > 15` -> shrink `left` -> `left = 1`, `sum = 7`
* `right = 3`: `sum = 14` -> `maxLen = 2`
* `right = 4`: `sum = 15` -> `maxLen = Math.max(2, 4 - 1 + 1) = 4` (Subarray: `[5, 2, 7, 1]`)
* Output: `4`

## 🔹 Important Java Difference
Prefix sums stored in HashMaps need to map to `Long` keys to prevent overflows during sum operations.

## 🔹 Common Mistakes
Shrinking window without keeping check `left <= right` boundary rule.

## 🔹 Placement / Interview Point
Extremely popular test problem. If array elements are only positive, sliding window $O(N)$ time with $O(1)$ space is the expected optimal solution.

## 🔹 Related Problems
* Subarray Sum Equals K (LeetCode 560).

## 🔹 Quick Revision
Maintain `left` and `right`. Keep adding to sum. If sum exceeds K, subtract `arr[left]` and increment `left`. Update max length when sum matches K.

---

# 14. Longest Subarray with Sum K

## 🔹 Problem Statement
Given an array `arr` of size `N` containing both positive and negative integers and a target sum `K`, find the length of the longest subarray with a sum equal to `K`.

## 🔹 What is Being Asked?
Array mein positive aur negative dono ranges ke numbers ho sakte hain. Humein sum K banane wala longest subarray trace karna hai.

## 🔹 Examples / Test Cases
| Input | Output |
|---|---|
| `arr = [-1, 1, 1]`, `k = 1` | `3` (Subarray `[-1, 1, 1]`) |

## 🔹 Constraints
* `1 <= arr.length <= 10^5`
* `-10^9 <= arr[i] <= 10^9`
* `-10^9 <= k <= 10^9`

## 🔹 C++ → Java Connection
* C++: `unordered_map`
* Java: `HashMap` (lookups are average $O(1)$).

### C++
```cpp
unordered_map<long long, int> preMap;
```
### Java
```java
HashMap<Long, Integer> preMap = new HashMap<>();
```

## 🔹 Pattern / Concept
Prefix Sum accumulation with HashMap tracking.

## 🔹 How to Think / Approach
Negative numbers array ranges mein include ho sakte hain, isliye sliding window logic failed ho jayegi (because sum is not monotonic anymore). Humein dynamic lookup hash tables structure select karna hoga. Har step par current prefix sum target logic: `sum - K` map mein check karenge.

## 🔹 Brute Force Approach
Generate all subarrays.
```java
class Solution {
    public int longestSubarray(int[] arr, int k) {
        int maxLen = 0;
        int n = arr.length;
        for (int i = 0; i < n; i++) {
            long sum = 0;
            for (int j = i; j < n; j++) {
                sum += arr[j];
                if (sum == k) {
                    maxLen = Math.max(maxLen, j - i + 1);
                }
            }
        }
        return maxLen;
    }
}
```
* **Time Complexity**: $O(N^2)$
* **Space Complexity**: $O(1)$

## 🔹 Optimal Approach
Prefix Sum tracking inside a HashMap.
```java
import java.util.HashMap;

class Solution {
    public int longestSubarray(int[] arr, int k) {
        HashMap<Long, Integer> map = new HashMap<>();
        long sum = 0;
        int maxLen = 0;
        
        for (int i = 0; i < arr.length; i++) {
            sum += arr[i];
            
            // Case 1: Subarray starting from index 0
            if (sum == k) {
                maxLen = i + 1;
            }
            
            // Case 2: check if (sum - k) prefix is found before
            long rem = sum - k;
            if (map.containsKey(rem)) {
                maxLen = Math.max(maxLen, i - map.get(rem));
            }
            
            // Store prefix index only if it does not already exist
            // This ensures we keep the leftmost index for maximum length
            if (!map.containsKey(sum)) {
                map.put(sum, i);
            }
        }
        return maxLen;
    }
}
```
* **Time Complexity**: $O(N)$ (average case using HashMap)
* **Space Complexity**: $O(N)$ (temp map storage)

## 🔹 Dry Run
Input: `arr = [-1, 1, 1]`, `k = 1`
* `i = 0`: `sum = -1` -> not equal to `1`. `rem = -1 - 1 = -2` (not in map). Put `(-1, 0)` in map.
* `i = 1`: `sum = 0` -> not equal to `1`. `rem = 0 - 1 = -1` (exists at index 0). `maxLen = Math.max(0, 1 - 0) = 1`. Put `(0, 1)` in map.
* `i = 2`: `sum = 1` -> equals `1` -> `maxLen = 2 + 1 = 3`. `rem = 1 - 1 = 0` (exists at index 1) -> `i - 1 = 1 < 3`. Put `(1, 2)` in map.
* Output: `3`

## 🔹 Important Java Difference
Ensure prefix sum is stored as `Long` to avoid integer ranges overflow during computations.

## 🔹 Common Mistakes
Overwriting prefix sums indexes in the map. If a prefix sum repeats (e.g., due to zero or negative loops), we must not update its index so that the window size remains maximum.

## 🔹 Placement / Interview Point
Crucial optimization problem. Showcases difference between Sliding Window (only for positives) vs Prefix Sum (for positives/negatives) constraints.

## 🔹 Related Problems
* Largest Subarray with 0 Sum.

## 🔹 Quick Revision
Maintain cumulative prefix sum. Check if `sum - K` prefix exists in the map. Only store index of prefix sum if it's encountered for the first time.

---

# 🎯 Final Striver Arrays Easy Checklist

- [ ] Largest Element
- [ ] Second Largest Element
- [ ] Check if the Array is Sorted II
- [ ] Remove Duplicates from Sorted Array
- [ ] Left Rotate Array by One
- [ ] Left Rotate Array by K Places
- [ ] Move Zeroes to End
- [ ] Linear Search
- [ ] Union of Two Sorted Arrays
- [ ] Find Missing Number
- [ ] Maximum Consecutive Ones
- [ ] Find the Number that Appears Once, and Other Numbers Twice
- [ ] Longest Subarray with Given Sum K (Positives)
- [ ] Longest Subarray with Sum K (Positives + Negatives)

---

# 🧠 Patterns Covered

- [x] Array Traversal
- [x] Min/Max Tracking
- [x] Cyclic Checking
- [x] Two Pointer
- [x] Shift Operations
- [x] Reversal Algorithm
- [x] Math Sum Formulas
- [x] XOR Operations
- [x] Sliding Window
- [x] Prefix Sum + HashMap
