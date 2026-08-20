# 50 Java Placement Coding Practice Questions

This document contains exactly 50 practice coding questions designed to bridge your C++ knowledge into Java coding mastery.

---

## 📂 Section 1: Java Basics & Arrays (Q1 - Q15)

### Q1: Print Fibonacci Series (Iterative)
*   **Problem Statement:** Return the N-th Fibonacci number.
*   **C++ Logic:** Loop and swap dynamic values.
*   **Java Approach:** Implement standard iteration using variables.
*   **Java Code:**
    ```java
    public int fibonacci(int n) {
        if (n <= 1) return n;
        int a = 0, b = 1;
        for (int i = 2; i <= n; i++) {
            int c = a + b;
            a = b;
            b = c;
        }
        return b;
    }
    ```
*   **Explanation:** Sum elements up to N using values.
*   **Expected Output:** `fibonacci(5) -> 5`
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Interview Point:** Handled iteratively to avoid $O(2^N)$ recursion overhead.
*   **Common Mistake:** Forgetting base cases for $N \le 1$.

---

### Q2: Sum of Elements in Array
*   **Problem Statement:** Find the sum of all elements in an array.
*   **C++ Logic:** `accumulate(arr.begin(), arr.end(), 0)`
*   **Java Approach:** Iteration loop.
*   **Java Code:**
    ```java
    public int sumArray(int[] arr) {
        int sum = 0;
        for (int num : arr) sum += num;
        return sum;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Common Mistake:** Subsum integer overflow. Use `long` if values are large.

---

### Q3: Max Element in Array
*   **Problem Statement:** Find the maximum element.
*   **C++ Logic:** `*max_element(arr, arr+n)`
*   **Java Approach:** Traverse, maintain local maximum.
*   **Java Code:**
    ```java
    public int findMax(int[] arr) {
        int max = Integer.MIN_VALUE;
        for (int num : arr) max = Math.max(max, num);
        return max;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q4: Reverse an Array (In-place)
*   **Problem Statement:** Reverse array elements in-place.
*   **C++ Logic:** `reverse(arr.begin(), arr.end())`
*   **Java Approach:** Two-pointer swap.
*   **Java Code:**
    ```java
    public void reverseArray(int[] arr) {
        int left = 0, right = arr.length - 1;
        while (left < right) {
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            left++; right--;
        }
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q5: Check if Array is Sorted
*   **Problem Statement:** Check if array is sorted in ascending order.
*   **C++ Logic:** Check `arr[i] <= arr[i+1]`.
*   **Java Approach:** Same logic.
*   **Java Code:**
    ```java
    public boolean isSorted(int[] arr) {
        for (int i = 0; i < arr.length - 1; i++) {
            if (arr[i] > arr[i+1]) return false;
        }
        return true;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q6: Count Even and Odd Numbers
*   **Problem Statement:** Return the count of even and odd integers.
*   **C++ Logic:** Modular arithmetic verification.
*   **Java Approach:** Scan and return inline array counts.
*   **Java Code:**
    ```java
    public int[] countEvenOdd(int[] arr) {
        int even = 0, odd = 0;
        for (int num : arr) {
            if (num % 2 == 0) even++;
            else odd++;
        }
        return new int[]{even, odd};
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q7: Find Index of Element (Linear Search)
*   **Problem Statement:** Return index of key or -1.
*   **C++ Logic:** Linear traversal search.
*   **Java Code:**
    ```java
    public int linearSearch(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) return i;
        }
        return -1;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q8: Find Average of Array Elements
*   **Problem Statement:** Calculate average values.
*   **Java Code:**
    ```java
    public double findAverage(int[] arr) {
        double sum = 0;
        for (int num : arr) sum += num;
        return sum / arr.length;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q9: Count Occurrences of Element
*   **Problem Statement:** Return counts of target element.
*   **Java Code:**
    ```java
    public int countOccurrences(int[] arr, int target) {
        int count = 0;
        for (int num : arr) {
            if (num == target) count++;
        }
        return count;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q10: Find Second Smallest Element
*   **Problem Statement:** Find second smallest element in array.
*   **Java Code:**
    ```java
    public int findSecondSmallest(int[] arr) {
        int smallest = Integer.MAX_VALUE;
        int secondSmallest = Integer.MAX_VALUE;
        for (int num : arr) {
            if (num < smallest) {
                secondSmallest = smallest;
                smallest = num;
            } else if (num < secondSmallest && num != smallest) {
                secondSmallest = num;
            }
        }
        return secondSmallest;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q11: Find Unique Elements (No Duplicates)
*   **Problem Statement:** Return unique items.
*   **Java Approach:** Use `HashSet`.
*   **Java Code:**
    ```java
    import java.util.HashSet;
    public int[] getUnique(int[] arr) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : arr) set.add(num);
        int[] res = new int[set.size()];
        int idx = 0;
        for (int num : set) res[idx++] = num;
        return res;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q12: Copy Elements to Another Array
*   **Problem Statement:** Replicate arrays.
*   **Java Code:**
    ```java
    import java.util.Arrays;
    public int[] copyArray(int[] arr) {
        return Arrays.copyOf(arr, arr.length);
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q13: Swap Elements in Array
*   **Problem Statement:** Swap elements at index $i$ and $j$.
*   **Java Code:**
    ```java
    public void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    ```
*   **Complexity:** Time: $O(1)$, Space: $O(1)$

---

### Q14: Print 2D Array Grid
*   **Problem Statement:** Print grid values row-by-row.
*   **Java Code:**
    ```java
    public void printGrid(int[][] grid) {
        for (int i = 0; i < grid.length; i++) {
            for (int j = 0; j < grid[i].length; j++) {
                System.out.print(grid[i][j] + " ");
            }
            System.out.println();
        }
    }
    ```
*   **Complexity:** Time: $O(R \times C)$, Space: $O(1)$

---

### Q15: Matrix Diagonal Sum
*   **Problem Statement:** Sum primary diagonal elements.
*   **Java Code:**
    ```java
    public int primaryDiagonalSum(int[][] grid) {
        int sum = 0;
        for (int i = 0; i < grid.length; i++) {
            sum += grid[i][i];
        }
        return sum;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

## 📂 Section 2: Strings, ArrayList & HashMaps (Q16 - Q30)

### Q16: Reverse a String
*   **Problem Statement:** Return the reversed string.
*   **Java Code:**
    ```java
    public String reverse(String s) {
        return new StringBuilder(s).reverse().toString();
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q17: Count Vowels and Consonants
*   **Problem Statement:** Return counts of vowels and consonants.
*   **Java Code:**
    ```java
    public int[] countVowelsConsonants(String s) {
        int v = 0, c = 0;
        s = s.toLowerCase();
        for (int i = 0; i < s.length(); i++) {
            char ch = s.charAt(i);
            if (ch >= 'a' && ch <= 'z') {
                if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') v++;
                else c++;
            }
        }
        return new int[]{v, c};
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q18: Check for Substring
*   **Problem Statement:** Verify if a string contains another.
*   **Java Code:**
    ```java
    public boolean containsSub(String s, String target) {
        return s.contains(target);
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q19: Count Words in a String
*   **Problem Statement:** Return the word count.
*   **Java Code:**
    ```java
    public int countWords(String s) {
        if (s == null || s.trim().isEmpty()) return 0;
        return s.trim().split("\\s+").length;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q20: First Non-Repeating Character
*   **Problem Statement:** Find first unique character index.
*   **Java Code:**
    ```java
    import java.util.HashMap;
    public int firstUniqChar(String s) {
        HashMap<Character, Integer> count = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            count.put(c, count.getOrDefault(c, 0) + 1);
        }
        for (int i = 0; i < s.length(); i++) {
            if (count.get(s.charAt(i)) == 1) return i;
        }
        return -1;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$ (limited alphabet sizes).

---

### Q21: Check if Anagram
*   **Problem Statement:** Check if s and t are anagrams.
*   **Java Code:**
    ```java
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] freq = new int[26];
        for (int i = 0; i < s.length(); i++) {
            freq[s.charAt(i) - 'a']++;
            freq[t.charAt(i) - 'a']--;
        }
        for (int count : freq) if (count != 0) return false;
        return true;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q22: Remove All Spaces
*   **Problem Statement:** Remove whitespaces.
*   **Java Code:**
    ```java
    public String removeSpaces(String s) {
        return s.replace(" ", "");
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q23: Print ArrayList Elements
*   **Problem Statement:** Print list content.
*   **Java Code:**
    ```java
    import java.util.ArrayList;
    public void printList(ArrayList<Integer> list) {
        for (int num : list) System.out.print(num + " ");
        System.out.println();
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q24: Check if List is Empty
*   **Problem Statement:** Verify sizing.
*   **Java Code:**
    ```java
    import java.util.ArrayList;
    public boolean checkEmpty(ArrayList<Integer> list) {
        return list.isEmpty();
    }
    ```
*   **Complexity:** Time: $O(1)$, Space: $O(1)$

---

### Q25: Frequency of Strings in List
*   **Problem Statement:** Map strings to occurrences.
*   **Java Code:**
    ```java
    import java.util.ArrayList;
    import java.util.HashMap;
    public HashMap<String, Integer> stringFreq(ArrayList<String> list) {
        HashMap<String, Integer> map = new HashMap<>();
        for (String s : list) {
            map.put(s, map.getOrDefault(s, 0) + 1);
        }
        return map;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q26: Remove Duplicates from ArrayList
*   **Problem Statement:** Keep unique items.
*   **Java Code:**
    ```java
    import java.util.ArrayList;
    import java.util.LinkedHashSet;
    public ArrayList<Integer> removeDuplicates(ArrayList<Integer> list) {
        LinkedHashSet<Integer> set = new LinkedHashSet<>(list);
        return new ArrayList<>(set);
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q27: Check Subset of Array
*   **Problem Statement:** Verify if B is subset of A.
*   **Java Code:**
    ```java
    import java.util.HashSet;
    public boolean isSubset(int[] a, int[] b) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : a) set.add(num);
        for (int num : b) {
            if (!set.contains(num)) return false;
        }
        return true;
    }
    ```
*   **Complexity:** Time: $O(N + M)$, Space: $O(N)$

---

### Q28: Intersection of Arrays using HashSet
*   **Problem Statement:** Return overlapping values.
*   **Java Code:**
    ```java
    import java.util.HashSet;
    import java.util.ArrayList;
    public int[] intersection(int[] a, int[] b) {
        HashSet<Integer> set1 = new HashSet<>();
        for (int num : a) set1.add(num);
        HashSet<Integer> intersect = new HashSet<>();
        for (int num : b) {
            if (set1.contains(num)) intersect.add(num);
        }
        int[] res = new int[intersect.size()];
        int idx = 0;
        for (int num : intersect) res[idx++] = num;
        return res;
    }
    ```
*   **Complexity:** Time: $O(N + M)$, Space: $O(N)$

---

### Q29: First Repeating Element
*   **Problem Statement:** Find the first element that repeats.
*   **Java Code:**
    ```java
    import java.util.HashSet;
    public int firstRepeating(int[] arr) {
        HashSet<Integer> set = new HashSet<>();
        int firstRep = -1;
        for (int i = arr.length - 1; i >= 0; i--) {
            if (set.contains(arr[i])) firstRep = arr[i];
            else set.add(arr[i]);
        }
        return firstRep;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q30: String Compression (Runs)
*   **Problem Statement:** Compress string e.g. "aabcc" to "a2b1c2".
*   **Java Code:**
    ```java
    public String compress(String s) {
        if (s == null || s.isEmpty()) return s;
        StringBuilder sb = new StringBuilder();
        int count = 1;
        for (int i = 1; i <= s.length(); i++) {
            if (i < s.length() && s.charAt(i) == s.charAt(i - 1)) {
                count++;
            } else {
                sb.append(s.charAt(i - 1)).append(count);
                count = 1;
            }
        }
        return sb.toString();
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

## 📂 Section 3: Core DSA Patterns (Q31 - Q40)

### Q31: Two Sum (Pointers Style)
*   **Problem Statement:** Check if pair exists with target sum in sorted array.
*   **Java Code:**
    ```java
    public boolean twoSumSorted(int[] arr, int target) {
        int i = 0, j = arr.length - 1;
        while (i < j) {
            int sum = arr[i] + arr[j];
            if (sum == target) return true;
            else if (sum < target) i++;
            else j--;
        }
        return false;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q32: Longest Subarray with Sum <= K (Sliding Window)
*   **Problem Statement:** Find length of longest subarray.
*   **Java Code:**
    ```java
    public int longestSubarray(int[] arr, int k) {
        int left = 0, sum = 0, maxLen = 0;
        for (int right = 0; right < arr.length; right++) {
            sum += arr[right];
            while (sum > k && left <= right) {
                sum -= arr[left++];
            }
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q33: Range Sum Query (Prefix Sum)
*   **Problem Statement:** Answer queries $Q(L, R)$ in $O(1)$ time.
*   **Java Code:**
    ```java
    public int[] precomputePrefix(int[] arr) {
        int[] pref = new int[arr.length];
        pref[0] = arr[0];
        for (int i = 1; i < arr.length; i++) {
            pref[i] = pref[i-1] + arr[i];
        }
        return pref;
    }
    public int querySum(int[] pref, int L, int R) {
        if (L == 0) return pref[R];
        return pref[R] - pref[L-1];
    }
    ```
*   **Complexity:** Time: $O(N)$ initialization, $O(1)$ query. Space: $O(N)$.

---

### Q34: Binary Search implementation
*   **Problem Statement:** Standard binary search.
*   **Java Code:**
    ```java
    public int binarySearch(int[] arr, int target) {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] == target) return mid;
            else if (arr[mid] < target) low = mid + 1;
            else high = mid - 1;
        }
        return -1;
    }
    ```
*   **Complexity:** Time: $O(\log N)$, Space: $O(1)$

---

### Q35: Kadane's Algorithm (Max Subarray Sum)
*   **Problem Statement:** Find largest subarray sum.
*   **Java Code:**
    ```java
    public int maxSubarraySum(int[] arr) {
        int max = Integer.MIN_VALUE, current = 0;
        for (int num : arr) {
            current += num;
            max = Math.max(max, current);
            if (current < 0) current = 0;
        }
        return max;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q36: Container With Most Water (Two Pointers)
*   **Problem Statement:** Maximize area $(j - i) \times \min(arr[i], arr[j])$.
*   **Java Code:**
    ```java
    public int maxArea(int[] height) {
        int left = 0, right = height.length - 1, max = 0;
        while (left < right) {
            int current = (right - left) * Math.min(height[left], height[right]);
            max = Math.max(max, current);
            if (height[left] < height[right]) left++;
            else right--;
        }
        return max;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q37: Subarray with Given Sum (Hashing)
*   **Problem Statement:** Check if subarray exists with sum $K$.
*   **Java Code:**
    ```java
    import java.util.HashSet;
    public boolean subarraySumEqualsK(int[] arr, int k) {
        HashSet<Integer> set = new HashSet<>();
        set.add(0);
        int sum = 0;
        for (int num : arr) {
            sum += num;
            if (set.contains(sum - k)) return true;
            set.add(sum);
        }
        return false;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q38: Find Peak Element (Binary Search style)
*   **Problem Statement:** Return index of local maximum.
*   **Java Code:**
    ```java
    public int findPeak(int[] arr) {
        int low = 0, high = arr.length - 1;
        while (low < high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] < arr[mid + 1]) low = mid + 1;
            else high = mid;
        }
        return low;
    }
    ```
*   **Complexity:** Time: $O(\log N)$, Space: $O(1)$

---

### Q39: Find Equilibrium Index
*   **Problem Statement:** Find index $i$ where prefix sum equals suffix sum.
*   **Java Code:**
    ```java
    public int findEquilibrium(int[] arr) {
        int totalSum = 0, leftSum = 0;
        for (int num : arr) totalSum += num;
        for (int i = 0; i < arr.length; i++) {
            totalSum -= arr[i];
            if (leftSum == totalSum) return i;
            leftSum += arr[i];
        }
        return -1;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q40: Count Subarrays with Odd Sum
*   **Problem Statement:** Return count of odd sum subarrays.
*   **Java Code:**
    ```java
    public int countOddSubarrays(int[] arr) {
        int oddCount = 0, evenCount = 1; // evenCount initialized to 1 for prefix sum = 0
        int currentSum = 0, total = 0;
        for (int num : arr) {
            currentSum += num;
            if (currentSum % 2 == 0) {
                total += oddCount;
                evenCount++;
            } else {
                total += evenCount;
                oddCount++;
            }
        }
        return total;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

## 📂 Section 4: Placement-Level Problems (Q41 - Q50)

### Q41: Merge Intervals
*   **Problem Statement:** Merge overlapping intervals.
*   **Java Code:**
    ```java
    import java.util.Arrays;
    import java.util.ArrayList;
    public int[][] merge(int[][] intervals) {
        if (intervals.length <= 1) return intervals;
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));
        ArrayList<int[]> list = new ArrayList<>();
        int[] current = intervals[0];
        list.add(current);
        for (int[] interval : intervals) {
            if (interval[0] <= current[1]) {
                current[1] = Math.max(current[1], interval[1]);
            } else {
                current = interval;
                list.add(current);
            }
        }
        return list.toArray(new int[list.size()][]);
    }
    ```
*   **Complexity:** Time: $O(N \log N)$, Space: $O(N)$ for sorting/output.

---

### Q42: Product of Array Except Self
*   **Problem Statement:** Calculate output where $res[i]$ is product of all elements except $arr[i]$. No division allowed.
*   **Java Code:**
    ```java
    public int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] res = new int[n];
        res[0] = 1;
        for (int i = 1; i < n; i++) {
            res[i] = res[i - 1] * nums[i - 1];
        }
        int right = 1;
        for (int i = n - 1; i >= 0; i--) {
            res[i] = res[i] * right;
            right *= nums[i];
        }
        return res;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$ auxiliary.

---

### Q43: Next Permutation
*   **Problem Statement:** Compute lexicographically next permutation.
*   **Java Code:**
    ```java
    public void nextPermutation(int[] nums) {
        int i = nums.length - 2;
        while (i >= 0 && nums[i] >= nums[i + 1]) i--;
        if (i >= 0) {
            int j = nums.length - 1;
            while (nums[j] <= nums[i]) j--;
            swap(nums, i, j);
        }
        reverse(nums, i + 1, nums.length - 1);
    }
    private void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    private void reverse(int[] arr, int l, int r) {
        while (l < r) swap(arr, l++, r--);
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q44: Longest Consecutive Sequence
*   **Problem Statement:** Length of longest consecutive elements sequence.
*   **Java Code:**
    ```java
    import java.util.HashSet;
    public int longestConsecutive(int[] nums) {
        HashSet<Integer> set = new HashSet<>();
        for (int num : nums) set.add(num);
        int max = 0;
        for (int num : nums) {
            if (!set.contains(num - 1)) {
                int currNum = num;
                int currStreak = 1;
                while (set.contains(currNum + 1)) {
                    currNum++;
                    currStreak++;
                }
                max = Math.max(max, currStreak);
            }
        }
        return max;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q45: Spiral Matrix Traversal
*   **Problem Statement:** Return list of elements in spiral order.
*   **Java Code:**
    ```java
    import java.util.ArrayList;
    import java.util.List;
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> res = new ArrayList<>();
        if (matrix.length == 0) return res;
        int top = 0, bottom = matrix.length - 1, left = 0, right = matrix[0].length - 1;
        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; i++) res.add(matrix[top][i]);
            top++;
            for (int i = top; i <= bottom; i++) res.add(matrix[i][right]);
            right--;
            if (top <= bottom) {
                for (int i = right; i >= left; i--) res.add(matrix[bottom][i]);
                bottom--;
            }
            if (left <= right) {
                for (int i = bottom; i >= top; i--) res.add(matrix[i][left]);
                left++;
            }
        }
        return res;
    }
    ```
*   **Complexity:** Time: $O(R \times C)$, Space: $O(1)$ auxiliary.

---

### Q46: Valid Parentheses (Stack)
*   **Problem Statement:** Check if braces match correctly.
*   **Java Code:**
    ```java
    import java.util.Stack;
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();
        for (char c : s.toCharArray()) {
            if (c == '(') stack.push(')');
            else if (c == '{') stack.push('}');
            else if (c == '[') stack.push(']');
            else if (stack.isEmpty() || stack.pop() != c) return false;
        }
        return stack.isEmpty();
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q47: Sort Colors (Sort 0s, 1s, 2s)
*   **Problem Statement:** Dutch national flag implementation.
*   **Java Code:**
    ```java
    public void sortColors(int[] nums) {
        int low = 0, mid = 0, high = nums.length - 1;
        while (mid <= high) {
            if (nums[mid] == 0) {
                int temp = nums[low];
                nums[low++] = nums[mid];
                nums[mid++] = temp;
            } else if (nums[mid] == 1) {
                mid++;
            } else {
                int temp = nums[mid];
                nums[mid] = nums[high];
                nums[high--] = temp;
            }
        }
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q48: Longest Substring Without Repeating Characters
*   **Problem Statement:** Length of longest unique characters substring.
*   **Java Code:**
    ```java
    import java.util.HashMap;
    public int lengthOfLongestSubstring(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        int left = 0, max = 0;
        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            if (map.containsKey(c)) {
                left = Math.max(left, map.get(c) + 1);
            }
            map.put(c, right);
            max = Math.max(max, right - left + 1);
        }
        return max;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(min(N, A))$ where $A$ is alphabet size.

---

### Q49: Rotate Image (Rotate Matrix 90 degrees)
*   **Problem Statement:** Rotate square matrix 90 degrees clockwise in place.
*   **Java Code:**
    ```java
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        for (int i = 0; i < n; i++) {
            int l = 0, r = n - 1;
            while (l < r) {
                int temp = matrix[i][l];
                matrix[i][l++] = matrix[i][r];
                matrix[i][r--] = temp;
            }
        }
    }
    ```
*   **Complexity:** Time: $O(N^2)$, Space: $O(1)$

---

### Q50: Subarray Sums Divisible by K
*   **Problem Statement:** Count subarrays whose sum is divisible by $K$.
*   **Java Code:**
    ```java
    import java.util.HashMap;
    public int subarraysDivByK(int[] nums, int k) {
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        int sum = 0, count = 0;
        for (int num : nums) {
            sum += num;
            int rem = sum % k;
            if (rem < 0) rem += k; // Handle negative remainders in Java
            if (map.containsKey(rem)) {
                count += map.get(rem);
            }
            map.put(rem, map.getOrDefault(rem, 0) + 1);
        }
        return count;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(K)$
*   **Common Mistake:** Forgetting that modulo operation in Java can yield negative outcomes (`-5 % 3 = -2`). Make sure to normalize negative remainders using `rem += k`.
