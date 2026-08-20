# Chapter 14 — Java for Striver Arrays ⭐⭐⭐

This chapter maps C++ DSA logic to Java for the major Striver Array problems. 

---

### 1. Largest and Second Largest Element

*   **C++ Approach:** Scan once, maintain `max` and `secondMax`.
*   **Java Mapping:** Same logic. Use `Integer.MIN_VALUE` for initialization.
*   **Syntax Required:** `Math.max()`, `Integer.MIN_VALUE`, `arr.length`.
*   **Java Solution:**
    ```java
    public int findSecondLargest(int[] arr) {
        int largest = Integer.MIN_VALUE;
        int secondLargest = Integer.MIN_VALUE;
        for (int num : arr) {
            if (num > largest) {
                secondLargest = largest;
                largest = num;
            } else if (num > secondLargest && num != largest) {
                secondLargest = num;
            }
        }
        return secondLargest == Integer.MIN_VALUE ? -1 : secondLargest;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Java-specific Trap:** Do not initialize `secondLargest` to `0` because array elements can be negative. Use `Integer.MIN_VALUE`.
*   **Interview Point:** Handled in a single pass without sorting.

---

### 2. Remove Duplicates from Sorted Array

*   **C++ Approach:** Two-pointer in-place write.
*   **Java Mapping:** Keep an index pointer `i` for unique elements.
*   **Syntax Required:** Array updates.
*   **Java Solution:**
    ```java
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
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Java-specific Trap:** Watch out for empty array edge case checking.
*   **Interview Point:** Modifies array in-place, returning the count of unique elements.

---

### 3. Rotate Array (Left/Right by K steps)

*   **C++ Approach:** Reverse three parts: first `k`, remaining, then all.
*   **Java Mapping:** Replicate helper reverse method.
*   **Syntax Required:** Modulo `k % n` to handle large values of $K$.
*   **Java Solution:**
    ```java
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k = k % n;
        reverse(nums, 0, n - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, n - 1);
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
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Java-specific Trap:** Forgetting `k = k % n` throws an out-of-bounds error.

---

### 4. Move Zeroes to End

*   **C++ Approach:** Two-pointer pointer swap.
*   **Java Mapping:** Write non-zero elements, fill rest with zero.
*   **Syntax Required:** Single pass iteration.
*   **Java Solution:**
    ```java
    public void moveZeroes(int[] nums) {
        int writeIdx = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[writeIdx++] = nums[i];
            }
        }
        while (writeIdx < nums.length) {
            nums[writeIdx++] = 0;
        }
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 5. Union & Intersection of Two Sorted Arrays

*   **C++ Approach:** Two-pointer traversal, merge-style.
*   **Java Mapping:** Use `ArrayList<Integer>` to collect union, convert to array or return list.
*   **Syntax Required:** `ArrayList`, autoboxing.
*   **Java Solution (Union):**
    ```java
    import java.util.ArrayList;
    
    public ArrayList<Integer> findUnion(int[] a, int[] b) {
        ArrayList<Integer> union = new ArrayList<>();
        int i = 0, j = 0;
        while (i < a.length && j < b.length) {
            if (a[i] <= b[j]) {
                if (union.isEmpty() || union.get(union.size() - 1) != a[i]) {
                    union.add(a[i]);
                }
                i++;
            } else {
                if (union.isEmpty() || union.get(union.size() - 1) != b[j]) {
                    union.add(b[j]);
                }
                j++;
            }
        }
        while (i < a.length) {
            if (union.isEmpty() || union.get(union.size() - 1) != a[i]) union.add(a[i]);
            i++;
        }
        while (j < b.length) {
            if (union.isEmpty() || union.get(union.size() - 1) != b[j]) union.add(b[j]);
            j++;
        }
        return union;
    }
    ```
*   **Complexity:** Time: $O(N + M)$, Space: $O(N + M)$ to return output.

---

### 6. Missing Number

*   **C++ Approach:** XOR all indices and elements.
*   **Java Mapping:** Direct replication of XOR operators.
*   **Java Solution:**
    ```java
    public int missingNumber(int[] nums) {
        int xor = nums.length;
        for (int i = 0; i < nums.length; i++) {
            xor = xor ^ i ^ nums[i];
        }
        return xor;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 7. Max Consecutive Ones & Single Number

*   **C++ Approach:** For Single Number, XOR elements.
*   **Java Mapping:** Direct XOR matching.
*   **Java Solution (Single Number):**
    ```java
    public int singleNumber(int[] nums) {
        int xor = 0;
        for (int num : nums) xor ^= num;
        return xor;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 8. Two Sum

*   **C++ Approach:** Hashing with indices.
*   **Java Mapping:** Use `HashMap<Integer, Integer>`.
*   **Syntax Required:** `containsKey()`, `put()`, `get()`.
*   **Java Solution:**
    ```java
    import java.util.HashMap;
    
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int needed = target - nums[i];
            if (map.containsKey(needed)) {
                return new int[]{map.get(needed), i};
            }
            map.put(nums[i], i);
        }
        return new int[]{};
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### 9. Sort 0s, 1s, and 2s (Dutch National Flag)

*   **C++ Approach:** Three-pointer partitions (`low`, `mid`, `high`).
*   **Java Mapping:** Direct variable tracking.
*   **Java Solution:**
    ```java
    public void sortColors(int[] nums) {
        int low = 0, mid = 0, high = nums.length - 1;
        while (mid <= high) {
            if (nums[mid] == 0) {
                swap(nums, low++, mid++);
            } else if (nums[mid] == 1) {
                mid++;
            } else {
                swap(nums, mid, high--);
            }
        }
    }
    
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 10. Majority Element (> N/2)

*   **C++ Approach:** Moore's Voting Algorithm.
*   **Java Mapping:** Use counting variable matching.
*   **Java Solution:**
    ```java
    public int majorityElement(int[] nums) {
        int count = 0, candidate = 0;
        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }
        return candidate;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 11. Kadane's Algorithm (Max Subarray Sum)

*   **C++ Approach:** Continuous cumulative sum tracking.
*   **Java Mapping:** (Detailed in Ch 6/Ch 13).
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 12. Best Time to Buy and Sell Stock

*   **C++ Approach:** Track minimum price, check max profit daily.
*   **Java Mapping:** Same logic.
*   **Java Solution:**
    ```java
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;
        for (int price : prices) {
            if (price < minPrice) {
                minPrice = price;
            } else {
                maxProfit = Math.max(maxProfit, price - minPrice);
            }
        }
        return maxProfit;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 13. Rearrange Array Elements by Sign

*   **C++ Approach:** Put positives at even indices, negatives at odd indices.
*   **Java Mapping:** Create dynamic index pointers for positive and negative positions.
*   **Java Solution:**
    ```java
    public int[] rearrangeArray(int[] nums) {
        int[] result = new int[nums.length];
        int pos = 0, neg = 1;
        for (int num : nums) {
            if (num > 0) {
                result[pos] = num;
                pos += 2;
            } else {
                result[neg] = num;
                neg += 2;
            }
        }
        return result;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$ for output.

---

### 14. Next Permutation

*   **C++ Approach:** Find break point, swap, reverse suffix.
*   **Java Mapping:** Replicate C++ `std::next_permutation` logic manually.
*   **Java Solution:**
    ```java
    public void nextPermutation(int[] nums) {
        int n = nums.length;
        int i = n - 2;
        while (i >= 0 && nums[i] >= nums[i + 1]) i--;
        
        if (i >= 0) {
            int j = n - 1;
            while (nums[j] <= nums[i]) j--;
            swap(nums, i, j);
        }
        reverse(nums, i + 1, n - 1);
    }
    
    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    
    private void reverse(int[] nums, int start, int end) {
        while (start < end) swap(nums, start++, end--);
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 15. Leaders in an Array

*   **C++ Approach:** Iterate from right to left, record local maximums.
*   **Java Mapping:** Collect in list, then reverse.
*   **Java Solution:**
    ```java
    import java.util.ArrayList;
    import java.util.Collections;
    
    public ArrayList<Integer> leaders(int[] arr) {
        ArrayList<Integer> result = new ArrayList<>();
        int n = arr.length;
        int maxFromRight = arr[n - 1];
        result.add(maxFromRight);
        
        for (int i = n - 2; i >= 0; i--) {
            if (arr[i] >= maxFromRight) {
                maxFromRight = arr[i];
                result.add(maxFromRight);
            }
        }
        Collections.reverse(result);
        return result;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$ auxiliary.

---

### 16. Longest Consecutive Sequence

*   **C++ Approach:** Insert all into `unordered_set`, count consecutive chains.
*   **Java Mapping:** Use `HashSet<Integer>`.
*   **Java Solution:**
    ```java
    import java.util.HashSet;
    
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : nums) set.add(num);
        
        int longest = 0;
        for (int num : nums) {
            if (!set.contains(num - 1)) { // Start of a chain
                int currentNum = num;
                int currentStreak = 1;
                while (set.contains(currentNum + 1)) {
                    currentNum++;
                    currentStreak++;
                }
                longest = Math.max(longest, currentStreak);
            }
        }
        return longest;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### 17. Set Matrix Zeroes

*   **C++ Approach:** Mark columns/rows using first row/col as indicators.
*   **Java Mapping:** Track state using booleans.
*   **Java Solution:**
    ```java
    public void setZeroes(int[][] matrix) {
        int rows = matrix.length, cols = matrix[0].length;
        boolean firstColZero = false;
        
        for (int i = 0; i < rows; i++) {
            if (matrix[i][0] == 0) firstColZero = true;
            for (int j = 1; j < cols; j++) {
                if (matrix[i][j] == 0) {
                    matrix[i][0] = 0;
                    matrix[0][j] = 0;
                }
            }
        }
        
        for (int i = rows - 1; i >= 0; i--) {
            for (int j = cols - 1; j >= 1; j--) {
                if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                    matrix[i][j] = 0;
                }
            }
            if (firstColZero) matrix[i][0] = 0;
        }
    }
    ```
*   **Complexity:** Time: $O(N \times M)$, Space: $O(1)$

---

### 18. Rotate Matrix (90 degrees)

*   **C++ Approach:** Transpose and reverse rows.
*   **Java Mapping:** Replicate transposition helper functions.
*   **Java Solution:**
    ```java
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        // Transpose
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        // Reverse rows
        for (int i = 0; i < n; i++) {
            int left = 0, right = n - 1;
            while (left < right) {
                int temp = matrix[i][left];
                matrix[i][left] = matrix[i][right];
                matrix[i][right] = temp;
                left++;
                right--;
            }
        }
    }
    ```
*   **Complexity:** Time: $O(N^2)$, Space: $O(1)$

---

### 19. Spiral Matrix

*   **C++ Approach:** Maintain 4 boundaries (`top`, `bottom`, `left`, `right`).
*   **Java Mapping:** Replicate layout.
*   **Java Solution:**
    ```java
    import java.util.ArrayList;
    import java.util.List;
    
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> result = new ArrayList<>();
        if (matrix.length == 0) return result;
        int top = 0, bottom = matrix.length - 1;
        int left = 0, right = matrix[0].length - 1;
        
        while (top <= bottom && left <= right) {
            for (int j = left; j <= right; j++) result.add(matrix[top][j]);
            top++;
            for (int i = top; i <= bottom; i++) result.add(matrix[i][right]);
            right--;
            
            if (top <= bottom) {
                for (int j = right; j >= left; j--) result.add(matrix[bottom][j]);
                bottom--;
            }
            if (left <= right) {
                for (int i = bottom; i >= top; i--) result.add(matrix[i][left]);
                left++;
            }
        }
        return result;
    }
    ```
*   **Complexity:** Time: $O(N \times M)$, Space: $O(1)$ auxiliary.

---

### 20. Pascal's Triangle

*   **C++ Approach:** Build rows iteratively.
*   **Java Mapping:** Use nested `ArrayList<List<Integer>>`.
*   **Java Solution:**
    ```java
    import java.util.ArrayList;
    import java.util.List;
    
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> triangle = new ArrayList<>();
        for (int i = 0; i < numRows; i++) {
            List<Integer> row = new ArrayList<>();
            for (int j = 0; j <= i; j++) {
                if (j == 0 || j == i) {
                    row.add(1);
                } else {
                    row.add(triangle.get(i - 1).get(j - 1) + triangle.get(i - 1).get(j));
                }
            }
            triangle.add(row);
        }
        return triangle;
    }
    ```
*   **Complexity:** Time: $O(numRows^2)$, Space: $O(numRows^2)$ for output.

---

### 21. Majority Element II (> N/3)

*   **C++ Approach:** Extended Moore's Voting Algorithm (2 candidates).
*   **Java Mapping:** Direct implementation.
*   **Java Solution:**
    ```java
    import java.util.ArrayList;
    import java.util.List;
    
    public List<Integer> majorityElement2(int[] nums) {
        int num1 = 0, num2 = 0, count1 = 0, count2 = 0;
        for (int num : nums) {
            if (num == num1) count1++;
            else if (num == num2) count2++;
            else if (count1 == 0) { num1 = num; count1 = 1; }
            else if (count2 == 0) { num2 = num; count2 = 1; }
            else { count1--; count2--; }
        }
        
        count1 = 0; count2 = 0;
        for (int num : nums) {
            if (num == num1) count1++;
            else if (num == num2) count2++;
        }
        
        List<Integer> result = new ArrayList<>();
        if (count1 > nums.length / 3) result.add(num1);
        if (count2 > nums.length / 3) result.add(num2);
        return result;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### 22. 3Sum

*   **C++ Approach:** Sort, fix first element, use Two Pointer for remaining.
*   **Java Mapping:** Use nested `List<List<Integer>>`.
*   **Java Solution:**
    ```java
    import java.util.Arrays;
    import java.util.ArrayList;
    import java.util.List;
    
    public List<List<Integer>> threeSum(int[] nums) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();
        
        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue; // Skip duplicates
            int left = i + 1, right = nums.length - 1;
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum == 0) {
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    while (left < right && nums[left] == nums[left + 1]) left++;
                    while (left < right && nums[right] == nums[right - 1]) right--;
                    left++; right--;
                } else if (sum < 0) left++;
                else right--;
            }
        }
        return result;
    }
    ```
*   **Complexity:** Time: $O(N^2)$, Space: $O(1)$ or $O(N)$ for sorting.

---

### 23. 4Sum

*   **C++ Approach:** Sort, fix 2 outer elements, two pointer search inner elements.
*   **Java Mapping:** Replicate nested loop structure.
*   **Java Solution:**
    ```java
    import java.util.Arrays;
    import java.util.ArrayList;
    import java.util.List;
    
    public List<List<Integer>> fourSum(int[] nums, int target) {
        Arrays.sort(nums);
        List<List<Integer>> result = new ArrayList<>();
        int n = nums.length;
        
        for (int i = 0; i < n - 3; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue;
            for (int j = i + 1; j < n - 2; j++) {
                if (j > i + 1 && nums[j] == nums[j - 1]) continue;
                int left = j + 1, right = n - 1;
                while (left < right) {
                    long sum = (long)nums[i] + nums[j] + nums[left] + nums[right]; // Avoid overflow
                    if (sum == target) {
                        result.add(Arrays.asList(nums[i], nums[j], nums[left], nums[right]));
                        while (left < right && nums[left] == nums[left + 1]) left++;
                        while (left < right && nums[right] == nums[right - 1]) right--;
                        left++; right--;
                    } else if (sum < target) left++;
                    else right--;
                }
            }
        }
        return result;
    }
    ```
*   **Complexity:** Time: $O(N^3)$, Space: $O(1)$

---

### 24. Merge Intervals

*   **C++ Approach:** Sort by starts, insert or expand interval.
*   **Java Mapping:** Use custom comparator sorting and `ArrayList<int[]>`.
*   **Java Solution:**
    ```java
    import java.util.Arrays;
    import java.util.ArrayList;
    
    public int[][] merge(int[][] intervals) {
        if (intervals.length <= 1) return intervals;
        
        // Sort by start times
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        
        ArrayList<int[]> merged = new ArrayList<>();
        int[] current = intervals[0];
        merged.add(current);
        
        for (int[] next : intervals) {
            if (next[0] <= current[1]) {
                current[1] = Math.max(current[1], next[1]); // Merge
            } else {
                current = next;
                merged.add(current);
            }
        }
        return merged.toArray(new int[merged.size()][]);
    }
    ```
*   **Complexity:** Time: $O(N \log N)$, Space: $O(N)$ for output representation.
*   **Java-specific Trap:** Converting `ArrayList<int[]>` to primitive array requires `merged.toArray(new int[merged.size()][])`.

---

### 25. Merge Sorted Arrays in Place

*   **C++ Approach:** Gap method or pointer swap.
*   **Java Mapping:** Swap from behind (if space is available at the end of the first array, i.e., LeetCode format).
*   **Java Solution (LeetCode format: nums1 has size m+n):**
    ```java
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m - 1;
        int j = n - 1;
        int k = m + n - 1;
        
        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
    ```
*   **Complexity:** Time: $O(M + N)$, Space: $O(1)$

---

### 26. Count Inversions

*   **C++ Approach:** Modified Merge Sort.
*   **Java Mapping:** Track counts during recursive splits.
*   **Java Solution:**
    ```java
    public int countInversions(int[] arr) {
        return mergeSort(arr, 0, arr.length - 1);
    }
    
    private int mergeSort(int[] arr, int l, int r) {
        int count = 0;
        if (l < r) {
            int mid = l + (r - l) / 2;
            count += mergeSort(arr, l, mid);
            count += mergeSort(arr, mid + 1, r);
            count += merge(arr, l, mid, r);
        }
        return count;
    }
    
    private int merge(int[] arr, int l, int mid, int r) {
        int[] left = Arrays.copyOfRange(arr, l, mid + 1);
        int[] right = Arrays.copyOfRange(arr, mid + 1, r + 1);
        int i = 0, j = 0, k = l, swaps = 0;
        
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                arr[k++] = left[i++];
            } else {
                arr[k++] = right[j++];
                swaps += (left.length - i);
            }
        }
        while (i < left.length) arr[k++] = left[i++];
        while (j < right.length) arr[k++] = right[j++];
        return swaps;
    }
    ```
*   **Complexity:** Time: $O(N \log N)$, Space: $O(N)$

---

### 27. Reverse Pairs

*   **C++ Approach:** Modified Merge Sort counting.
*   **Java Mapping:** Same logic.
*   **Java Solution:**
    ```java
    public int reversePairs(int[] nums) {
        return mergeSortAndCount(nums, 0, nums.length - 1);
    }

    private int mergeSortAndCount(int[] nums, int l, int r) {
        if (l >= r) return 0;
        int mid = l + (r - l) / 2;
        int count = mergeSortAndCount(nums, l, mid) + mergeSortAndCount(nums, mid + 1, r);
        
        // Count reverse pairs
        int j = mid + 1;
        for (int i = l; i <= mid; i++) {
            while (j <= r && (long) nums[i] > 2L * nums[j]) {
                j++;
            }
            count += (j - (mid + 1));
        }
        
        // Merge helper
        Arrays.sort(nums, l, r + 1); // Simple sorted fallback (use standard merge for strictly O(N) merge step)
        return count;
    }
    ```
*   **Complexity:** Time: $O(N \log^2 N)$ using simple sort fallback, or $O(N \log N)$ with custom merge sorting. Space: $O(N)$.
*   **Java-specific Trap:** Cast to `(long)` to avoid overflow when checking `2 * nums[j]`.

---

### 10. Common Mistakes
*   **Int Overflow in Sums:** In 4Sum, adding multiple integers can trigger overflow. Cast the accumulation base to `(long)`.
*   **Comparator Syntax:** Using `(a, b) -> a - b` in interval merging causes problems if a coordinate is negative. Always use `Integer.compare(a, b)`.
