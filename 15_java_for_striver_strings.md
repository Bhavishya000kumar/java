# Chapter 15 — Java for Striver Strings ⭐⭐⭐

This chapter maps C++ DSA logic to Java for the major Striver String problems.

---

### 1. Reverse String & Palindrome Check

*   **C++ Approach:** Two-pointer swap.
*   **Java Mapping:** Since Java Strings are immutable, use `StringBuilder` for reversing or check indices directly using `charAt()`.
*   **Java Solution (Palindrome Check):**
    ```java
    public boolean isPalindrome(String s) {
        int i = 0, j = s.length() - 1;
        while (i < j) {
            while (i < j && !Character.isLetterOrDigit(s.charAt(i))) i++;
            while (i < j && !Character.isLetterOrDigit(s.charAt(j))) j--;
            if (Character.toLowerCase(s.charAt(i)) != Character.toLowerCase(s.charAt(j))) {
                return false;
            }
            i++;
            j--;
        }
        return true;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$
*   **Java-specific Trap:** Do not write `s.reverse()`. The `String` class does not have a `reverse()` method. Convert to `StringBuilder` or use index matching.

---

### 2. Valid Anagram

*   **C++ Approach:** Frequency map (using `vector<int>` size 26 or `unordered_map`).
*   **Java Mapping:** Use primitive `int[26]` frequency array.
*   **Java Solution:**
    ```java
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] freq = new int[26];
        for (int i = 0; i < s.length(); i++) {
            freq[s.charAt(i) - 'a']++;
            freq[t.charAt(i) - 'a']--;
        }
        for (int count : freq) {
            if (count != 0) return false;
        }
        return true;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$ (constant size 26 array).

---

### 3. Remove Outermost Parentheses

*   **C++ Approach:** Track depth using parentheses counter.
*   **Java Mapping:** Use `StringBuilder` to collect the result.
*   **Java Solution:**
    ```java
    public String removeOuterParentheses(String s) {
        StringBuilder sb = new StringBuilder();
        int opened = 0;
        for (char c : s.toCharArray()) {
            if (c == '(' && opened++ > 0) sb.append(c);
            if (c == ')' && opened-- > 1) sb.append(c);
        }
        return sb.toString();
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$ for output.

---

### 4. Largest Odd Number in String

*   **C++ Approach:** Scan from right to left, find first odd digit, return substring.
*   **Java Mapping:** Same logic. Use `.substring(0, i + 1)`.
*   **Java Solution:**
    ```java
    public String largestOddNumber(String num) {
        for (int i = num.length() - 1; i >= 0; i--) {
            int digit = num.charAt(i) - '0';
            if (digit % 2 != 0) {
                return num.substring(0, i + 1);
            }
        }
        return "";
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$ auxiliary.
*   **Java-specific Trap:** Substring extraction end index is exclusive, so use `i + 1`.

---

### 5. Longest Common Prefix

*   **C++ Approach:** Sort the string array, compare first and last strings.
*   **Java Mapping:** Use `Arrays.sort(strs)`.
*   **Java Solution:**
    ```java
    import java.util.Arrays;
    
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return "";
        Arrays.sort(strs);
        String first = strs[0];
        String last = strs[strs.length - 1];
        
        int i = 0;
        while (i < first.length() && i < last.length()) {
            if (first.charAt(i) == last.charAt(i)) {
                i++;
            } else {
                break;
            }
        }
        return first.substring(0, i);
    }
    ```
*   **Complexity:** Time: $O(N \log N \times L)$ where $L$ is length of longest string (due to sorting). Space: $O(1)$ auxiliary.

---

### 6. Isomorphic Strings

*   **C++ Approach:** Dual character frequency mapping.
*   **Java Mapping:** Use `int[256]` arrays to track the last seen index of characters.
*   **Java Solution:**
    ```java
    public boolean isIsomorphic(String s, String t) {
        int[] mapS = new int[256];
        int[] mapT = new int[256];
        
        for (int i = 0; i < s.length(); i++) {
            char charS = s.charAt(i);
            char charT = t.charAt(i);
            
            if (mapS[charS] != mapT[charT]) {
                return false;
            }
            
            mapS[charS] = i + 1;
            mapT[charT] = i + 1;
        }
        return true;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$ auxiliary.

---

### 7. Rotate String (Check if S is rotation of T)

*   **C++ Approach:** Check if `T` is a substring of `S + S`.
*   **Java Mapping:** Verify string length matching, check `(s + s).contains(t)`.
*   **Java Solution:**
    ```java
    public boolean rotateString(String s, String goal) {
        return s.length() == goal.length() && (s + s).contains(goal);
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(N)$ (for creating concatenated string).

---

### 8. Sort Characters By Frequency

*   **C++ Approach:** Frequency map + Priority Queue of pairs.
*   **Java Mapping:** Use custom class or frequency mapping combined with sorting list buckets.
*   **Java Solution:**
    ```java
    import java.util.HashMap;
    import java.util.ArrayList;
    import java.util.List;
    
    public String frequencySort(String s) {
        HashMap<Character, Integer> map = new HashMap<>();
        for (char c : s.toCharArray()) {
            map.put(c, map.getOrDefault(c, 0) + 1);
        }
        
        List<Character> chars = new ArrayList<>(map.keySet());
        // Sort descending by frequency
        chars.sort((a, b) -> map.get(b) - map.get(a));
        
        StringBuilder sb = new StringBuilder();
        for (char c : chars) {
            int freq = map.get(c);
            for (int i = 0; i < freq; i++) {
                sb.append(c);
            }
        }
        return sb.toString();
    }
    ```
*   **Complexity:** Time: $O(N + K \log K)$ where $K$ is number of unique characters. Space: $O(K)$.

---

### 9. Longest Substring Without Repeating Characters

*   **C++ Approach:** Sliding window using hash map to store last index.
*   **Java Mapping:** Use `int[256]` or `HashMap<Character, Integer>`.
*   **Java Solution:**
    ```java
    import java.util.Arrays;
    
    public int lengthOfLongestSubstring(String s) {
        int[] lastIndex = new int[256];
        Arrays.fill(lastIndex, -1);
        int maxLen = 0, left = 0;
        
        for (int right = 0; right < s.length(); right++) {
            char c = s.charAt(right);
            if (lastIndex[c] >= left) {
                left = lastIndex[c] + 1; // Shrink window
            }
            lastIndex[c] = right;
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$ auxiliary.

---

### 10. String Compression

*   **C++ Approach:** In-place modification of character values.
*   **Java Mapping:** Same logic. Update primitive characters in `char[]` and return new size.
*   **Java Solution:**
    ```java
    public int compress(char[] chars) {
        int i = 0, indexAns = 0;
        while (i < chars.length) {
            char currentChar = chars[i];
            int count = 0;
            while (i < chars.length && chars[i] == currentChar) {
                i++;
                count++;
            }
            chars[indexAns++] = currentChar;
            if (count > 1) {
                for (char c : Integer.toString(count).toCharArray()) {
                    chars[indexAns++] = c;
                }
            }
        }
        return indexAns;
    }
    ```
*   **Complexity:** Time: $O(N)$, Space: $O(1)$ auxiliary.
*   **Java-specific Trap:** Convert count to string and insert individual characters sequentially.

---

### 11. Common Mistakes
*   **Slow concats in loops:** Avoid `res += s.charAt(i)` inside nested loops. Always use `StringBuilder sb` and `sb.append()`.
*   **Direct comparisons:** Comparing chars using `equals()` instead of primitives. A `char` can be compared using `==`, but `String` must be compared using `.equals()`.
