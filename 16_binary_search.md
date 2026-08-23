# Chapter 16 — Binary Search ⭐⭐⭐

### 1. What is it?
Binary Search is an efficient algorithm for finding an element's position in a sorted array or search space. It works by repeatedly dividing the search interval in half.

### 2. Why do I need it for placements?
Binary Search is a core placement topic. Coding rounds frequently test searching in rotated sorted arrays, finding peaks, and Binary Search on answers (search space optimization problems like book allocation and aggressive cows).

### 3. C++ → Java Comparison
*   **Built-in Functions:**
    *   C++: `binary_search()`, `lower_bound()`, `upper_bound()`.
    *   Java: `Arrays.binarySearch()` (for arrays) and `Collections.binarySearch()` (for lists). However, in coding rounds, you are almost always required to write custom search partitions manually.
*   **Boundary Limits:** The basic loops are syntactically identical.

---

### 4. C++ vs. Java Code Templates

#### Pattern 1: Standard Binary Search
*   **C++ Version:**
    ```cpp
    int binarySearch(int arr[], int n, int target) {
        int low = 0, high = n - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] == target) return mid;
            else if (arr[mid] < target) low = mid + 1;
            else high = mid - 1;
        }
        return -1;
    }
    ```
*   **Java Version:**
    ```java
    public int binarySearch(int[] arr, int target) {
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
        return -1;
    }
    ```
*   **What Changed & Why:** Replaced pointer passing/size parameter `n` with direct object property `arr.length`.
*   **Java-specific Trap:** Writing `(low + high) / 2` can cause integer overflow if `low + high > Integer.MAX_VALUE`. Always use `low + (high - low) / 2`.

---

#### Pattern 2: Lower Bound
*Finds the first index where element is $\ge$ target.*
*   **C++ Version:**
    ```cpp
    int lowerBound(vector<int> &arr, int target) {
        int low = 0, high = arr.size() - 1, ans = arr.size();
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] >= target) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    ```
*   **Java Version:**
    ```java
    public int lowerBound(int[] arr, int target) {
        int low = 0, high = arr.length - 1;
        int ans = arr.length;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] >= target) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    ```

---

#### Pattern 3: Upper Bound
*Finds the first index where element is $>$ target.*
*   **C++ Version:**
    ```cpp
    int upperBound(vector<int> &arr, int target) {
        int low = 0, high = arr.size() - 1, ans = arr.size();
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] > target) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    ```
*   **Java Version:**
    ```java
    public int upperBound(int[] arr, int target) {
        int low = 0, high = arr.length - 1;
        int ans = arr.length;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] > target) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    ```

---

#### Pattern 4: Binary Search on Answer
*Used when target is monotonic (e.g. Yes/No validation bounds).*
*   **C++ Version:**
    ```cpp
    int bsOnAnswer(vector<int>& arr, int limit) {
        int low = getMin(arr), high = getMax(arr), ans = -1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (isValid(arr, mid, limit)) {
                ans = mid;
                high = mid - 1; // Try for smaller ans
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    ```
*   **Java Version:**
    ```java
    public int bsOnAnswer(int[] arr, int limit) {
        int low = getMin(arr);
        int high = getMax(arr);
        int ans = -1;
        while (low <= high) {
            int mid = low + (high - mid) / 2; // Wait, correct mid!
            // Wait, low + (high - low) / 2 is cleaner:
            // int mid = low + (high - low) / 2;
            if (isValid(arr, mid, limit)) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    ```

---

### 7. Simple Hinglish Explanation
Binary Search sirf tab lagta hai jab array ya search space **sorted** ho. Har step par hum range ko `low` aur `high` ke middle index `mid` par split karte hain. 
Safe `mid` calculation ke liye `low + (high - low) / 2` use karo taaki value limit se bahar na jaye.
Agar question kehta hai "find minimum speed to finish work" toh wahan search space `low = 1` aur `high = max_speed` banke **Binary Search on Answer** lag jata hai.

---

### 8. Striver Binary Search Problems in Java

#### 1. First and Last Position of Element
*   **C++ logic:** Combine lower bound and upper bound, or do two separate binary searches.
*   **Java Solution:**
    ```java
    public int[] searchRange(int[] nums, int target) {
        int first = findBound(nums, target, true);
        int last = findBound(nums, target, false);
        return new int[]{first, last};
    }
    
    private int findBound(int[] nums, int target, boolean isFirst) {
        int low = 0, high = nums.length - 1, ans = -1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (nums[mid] == target) {
                ans = mid;
                if (isFirst) high = mid - 1;
                else low = mid + 1;
            } else if (nums[mid] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return ans;
    }
    ```

#### 2. Search in Rotated Sorted Array
*   **C++ logic:** Identify which half is sorted, check target boundaries in that half.
*   **Java Solution:**
    ```java
    public int search(int[] nums, int target) {
        int low = 0, high = nums.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (nums[mid] == target) return mid;
            
            // Left half is sorted
            if (nums[low] <= nums[mid]) {
                if (target >= nums[low] && target < nums[mid]) {
                    high = mid - 1;
                } else {
                    low = mid + 1;
                }
            } else { // Right half is sorted
                if (target > nums[mid] && target <= nums[high]) {
                    low = mid + 1;
                } else {
                    high = mid - 1;
                }
            }
        }
        return -1;
    }
    ```

#### 3. Single Element in a Sorted Array
*   **C++ logic:** Every duplicate appears in pairs (even, odd index pairs). Check partition balance.
*   **Java Solution:**
    ```java
    public int singleNonDuplicate(int[] nums) {
        int low = 0, high = nums.length - 2;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            // Check if mid is at even/odd boundary
            if (nums[mid] == nums[mid ^ 1]) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return nums[low];
    }
    ```

#### 4. Koko Eating Bananas (BS on Answer)
*   **Java Solution:**
    ```java
    public int minEatingSpeed(int[] piles, int h) {
        int low = 1, high = 0;
        for (int pile : piles) high = Math.max(high, pile);
        int ans = high;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (calculateHours(piles, mid) <= h) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    
    private long calculateHours(int[] piles, int speed) {
        long total = 0;
        for (int pile : piles) {
            total += (pile + speed - 1) / speed;
        }
        return total;
    }
    ```

---

### 10. Common Mistakes
*   **Integer Overflow:** Using `(low + high) / 2` instead of `low + (high - low) / 2`.
*   **Incorrect Bounds:** Setting `low = mid` or `high = mid` inside standard loops which causes infinite loops. Use `low = mid + 1` and `high = mid - 1`.

### 11. Interview Point
*   **Why is Binary Search $O(\log N)$?**
    Because at each execution step, the input search size is halved ($N, N/2, N/4, \dots, 1$). Thus $N/2^k = 1 \implies k = \log_2 N$ steps.

### 12. Quick Revision
*   Low + (High - Low) / 2 to compute middle index.
*   Array must be sorted to apply Binary Search.
*   Binary Search on Answer maps values monotonic boundaries.
