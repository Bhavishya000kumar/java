# 50 Java Placement Coding Practice Questions

This document contains exactly 50 practice coding questions designed to bridge your C++ knowledge into Java coding mastery.

---

## 📂 Section 1: Java Basics & Arrays (Q1 - Q10)

### Q1: Print Fibonacci Series (Iterative)
*   **Problem Statement:** Return the N-th Fibonacci number.
*   **C++ Logic:** Loop and swap dynamic values.
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
*   **Explanation:** Sum elements up to N using variables.
*   **Expected Output:** `fibonacci(5) -> 5`
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Interview Point:** Handled iteratively to avoid $O(2^N)$ recursion overhead.
*   **Common Mistake:** Forgetting base cases for $N \le 1$.

---

### Q2: Sum of Elements in Array
*   **Problem Statement:** Find the sum of all elements in an array.
*   **C++ Logic:** `accumulate(arr.begin(), arr.end(), 0)`
*   **Java Code:**
    ```java
    public int sumArray(int[] arr) {
        int sum = 0;
        for (int num : arr) sum += num;
        return sum;
    }
    ```
*   **Explanation:** Iterate and accumulate.
*   **Expected Output:** `sumArray({1, 2, 3}) -> 6`
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Interview Point:** Use `long` if total sum exceeds integer boundaries.
*   **Common Mistake:** Subsum integer overflow.

---

### Q3: Max Element in Array
*   **Problem Statement:** Find the maximum element.
*   **C++ Logic:** `*max_element(arr, arr+n)`
*   **Java Code:**
    ```java
    public int findMax(int[] arr) {
        int max = Integer.MIN_VALUE;
        for (int num : arr) max = Math.max(max, num);
        return max;
    }
    ```
*   **Explanation:** Iterate, updating local maximum using `Math.max()`.
*   **Expected Output:** `findMax({1, 5, 3}) -> 5`
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Interview Point:** Initializing with `Integer.MIN_VALUE` rather than `0` (handles negative numbers).

---

### Q4: Reverse an Array (In-place)
*   **Problem Statement:** Reverse array elements in-place.
*   **C++ Logic:** `reverse(arr.begin(), arr.end())`
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
*   **Common Mistake:** Iterating until `arr.length` instead of midpoint, reversing it back.

---

### Q5: Check if Array is Sorted
*   **Problem Statement:** Check if array is sorted in ascending order.
*   **C++ Logic:** Check `arr[i] <= arr[i+1]`.
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
*   **Interview Point:** Shows returning inline arrays in Java (`new int[]{}`).

---

### Q7: Find Index of Element (Linear Search)
*   **Problem Statement:** Return index of key or -1.
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
*   **Common Mistake:** Doing integer division `sum / arr.length` if `sum` is defined as `int`. Define `sum` as `double` or cast it.

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

## 📂 Section 2: Strings, ArrayList & HashMaps (Q11 - Q20)

### Q11: Reverse a String
*   **Problem Statement:** Return the reversed string.
*   **Java Code:**
    ```java
    public String reverse(String s) {
        return new StringBuilder(s).reverse().toString();
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q12: Count Vowels and Consonants
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

### Q13: Check for Substring
*   **Problem Statement:** Verify if a string contains another.
*   **Java Code:**
    ```java
    public boolean containsSub(String s, String target) {
        return s.contains(target);
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q14: Count Words in a String
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

### Q15: First Non-Repeating Character
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
*   **Complexity:** Time: $O(N)$, Space: $O(1)$

---

### Q16: Check if Anagram
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

### Q17: Remove All Spaces
*   **Problem Statement:** Remove whitespaces.
*   **Java Code:**
    ```java
    public String removeSpaces(String s) {
        return s.replace(" ", "");
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q18: Print ArrayList Elements
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

### Q19: Check if List is Empty
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

### Q20: Frequency of Strings in List
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

## 📂 Section 3: Pointers, Sliding Window, Prefix Sum & Kadane (Q21 - Q30)

### Q21: Two Sum (Pointers Style)
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

### Q22: Longest Subarray with Sum <= K (Sliding Window)
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

### Q23: Range Sum Query (Prefix Sum)
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

### Q24: Kadane's Algorithm (Max Subarray Sum)
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

### Q25: Container With Most Water (Two Pointers)
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

### Q26: Subarray with Given Sum (Hashing)
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

### Q27: Find Equilibrium Index
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

### Q28: Count Subarrays with Odd Sum
*   **Problem Statement:** Return count of odd sum subarrays.
*   **Java Code:**
    ```java
    public int countOddSubarrays(int[] arr) {
        int oddCount = 0, evenCount = 1;
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

### Q29: Remove Duplicates from ArrayList
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

### Q30: Intersection of Arrays using HashSet
*   **Problem Statement:** Return overlapping values.
*   **Java Code:**
    ```java
    import java.util.HashSet;
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

## 📂 Section 4: Binary Search Problems (Q31 - Q40)

### Q31: Standard Binary Search
*   **Problem Statement:** Return target element index in sorted array or -1.
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

### Q32: Lower Bound Implementation
*   **Problem Statement:** First index of element $\ge$ target.
*   **Java Code:**
    ```java
    public int lowerBound(int[] arr, int target) {
        int low = 0, high = arr.length - 1, ans = arr.length;
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
*   **Complexity:** Time: $O(\log N)$, Space: $O(1)$

---

### Q33: Upper Bound Implementation
*   **Problem Statement:** First index of element $>$ target.
*   **Java Code:**
    ```java
    public int upperBound(int[] arr, int target) {
        int low = 0, high = arr.length - 1, ans = arr.length;
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
*   **Complexity:** Time: $O(\log N)$, Space: $O(1)$

---

### Q34: First and Last Position of Element
*   **Problem Statement:** Find boundaries of target element.
*   **Java Code:**
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
*   **Complexity:** Time: $O(\log N)$, Space: $O(1)$

---

### Q35: Search in Rotated Sorted Array
*   **Problem Statement:** Search target element in rotated sorted array.
*   **Java Code:**
    ```java
    public int search(int[] nums, int target) {
        int low = 0, high = nums.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (nums[mid] == target) return mid;
            if (nums[low] <= nums[mid]) {
                if (target >= nums[low] && target < nums[mid]) high = mid - 1;
                else low = mid + 1;
            } else {
                if (target > nums[mid] && target <= nums[high]) low = mid + 1;
                else high = mid - 1;
            }
        }
        return -1;
    }
    ```
*   **Complexity:** Time: $O(\log N)$, Space: $O(1)$

---

### Q36: Find Peak Element
*   **Problem Statement:** Find index of local maximum.
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

### Q37: Square Root of Integer
*   **Problem Statement:** Floor square root of N.
*   **Java Code:**
    ```java
    public int mySqrt(int x) {
        if (x == 0 || x == 1) return x;
        int low = 1, high = x, ans = 0;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (mid <= x / mid) {
                ans = mid;
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return ans;
    }
    ```
*   **Complexity:** Time: $O(\log N)$, Space: $O(1)$

---

### Q38: Single Element in Sorted Array
*   **Problem Statement:** Find element that appears once in a pair array.
*   **Java Code:**
    ```java
    public int singleNonDuplicate(int[] nums) {
        int low = 0, high = nums.length - 2;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (nums[mid] == nums[mid ^ 1]) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        return nums[low];
    }
    ```
*   **Complexity:** Time: $O(\log N)$, Space: $O(1)$

---

### Q39: Koko Eating Bananas (BS on Answer)
*   **Problem Statement:** Minimum eating speed to finish within $H$ hours.
*   **Java Code:**
    ```java
    public int minEatingSpeed(int[] piles, int h) {
        int low = 1, high = 1000000000;
        int ans = high;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (canEatAll(piles, mid, h)) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    private boolean canEatAll(int[] piles, int speed, int h) {
        long hours = 0;
        for (int pile : piles) {
            hours += (pile + speed - 1) / speed;
        }
        return hours <= h;
    }
    ```
*   **Complexity:** Time: $O(N \log(\max(\text{piles})))$, Space: $O(1)$

---

### Q40: Capacity to Ship Packages (BS on Answer)
*   **Problem Statement:** Minimum capacity of ship to deliver packages in $D$ days.
*   **Java Code:**
    ```java
    public int shipWithinDays(int[] weights, int days) {
        int low = 0, high = 0;
        for (int w : weights) {
            low = Math.max(low, w);
            high += w;
        }
        int ans = high;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (canShip(weights, mid, days)) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
    private boolean canShip(int[] weights, int capacity, int days) {
        int currentDays = 1, currentWeight = 0;
        for (int w : weights) {
            if (currentWeight + w > capacity) {
                currentDays++;
                currentWeight = 0;
            }
            currentWeight += w;
        }
        return currentDays <= days;
    }
    ```
*   **Complexity:** Time: $O(N \log(\text{sum} - \text{max}))$, Space: $O(1)$

---

## 📂 Section 5: Recursion Problems (Q41 - Q45)

### Q41: Print 1 to N using Recursion
*   **Problem Statement:** Print numbers from 1 to N without loops.
*   **Java Code:**
    ```java
    public void print1ToN(int n) {
        if (n == 0) return;
        print1ToN(n - 1);
        System.out.print(n + " ");
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$ (recursion stack).

---

### Q42: Factorial of a Number
*   **Problem Statement:** Calculate factorial.
*   **Java Code:**
    ```java
    public int factorial(int n) {
        if (n <= 1) return 1;
        return n * factorial(n - 1);
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$

---

### Q43: Generate Subsequences (Include / Exclude)
*   **Problem Statement:** Return all subsequences.
*   **Java Code:**
    ```java
    import java.util.ArrayList;
    import java.util.List;
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        solve(0, new ArrayList<>(), nums, ans);
        return ans;
    }
    private void solve(int idx, List<Integer> ds, int[] nums, List<List<Integer>> ans) {
        if (idx == nums.length) {
            ans.add(new ArrayList<>(ds)); // Deep copy!
            return;
        }
        ds.add(nums[idx]); // Pick
        solve(idx + 1, ds, nums, ans);
        ds.remove(ds.size() - 1); // Backtrack
        solve(idx + 1, ds, nums, ans); // Not Pick
    }
    ```
*   **Complexity:** Time: $O(2^N \times N)$, Space: $O(N)$

---

### Q44: Subset Sum Validation (Recursive)
*   **Problem Statement:** Check if subset with sum $K$ exists.
*   **Java Code:**
    ```java
    public boolean checkSubsetSum(int idx, int sum, int[] arr, int target) {
        if (sum == target) return true;
        if (idx == arr.length || sum > target) return false;
        
        // Pick
        if (checkSubsetSum(idx + 1, sum + arr[idx], arr, target)) return true;
        // Not Pick
        return checkSubsetSum(idx + 1, sum, arr, target);
    }
    ```
*   **Complexity:** Time: $O(2^N)$, Space: $O(N)$

---

### Q45: Basic Permutations Generation
*   **Problem Statement:** Generate all unique permutations.
*   **Java Code:**
    ```java
    import java.util.ArrayList;
    import java.util.List;
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
            swap(nums, idx, i); // Backtrack
        }
    }
    private void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    ```
*   **Complexity:** Time: $O(N! \times N)$, Space: $O(N)$

---

## 📂 Section 6: Placement-Level Mixed Problems (Q46 - Q50)

### Q46: Merge Intervals
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
*   **Complexity:** Time: $O(N \log N)$, Space: $O(N)$

---

### Q47: Product of Array Except Self
*   **Problem Statement:** Return array where $res[i]$ is product of all elements except $arr[i]$.
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

### Q48: Next Permutation
*   **Problem Statement:** Next lexicographical permutation.
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

### Q49: Spiral Matrix Traversal
*   **Problem Statement:** Spiral matrix elements output list.
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

### Q50: Valid Parentheses (Stack)
*   **Problem Statement:** Verify brace matching validity.
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
*   **Interview Point:** Handled via Stack mapping closing parentheses immediately.
*   **Common Mistake:** Forgetting to run `.isEmpty()` check at the end.
