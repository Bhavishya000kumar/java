# Chapter 12 — Sorting & Java Utilities

### 1. What is it?
Java provides built-in methods for sorting arrays and collection lists, along with utilities under the `Math` class for mathematical operations, and constant limits under the wrapper classes.

### 2. Why do I need it for placements?
Greedy algorithms, interval problems (like Merge Intervals), and custom optimization lookups require custom sorting (e.g. sorting by starting time). Mathematical helpers like `Math.max()` and boundary limits like `Integer.MIN_VALUE` are used in almost every DSA solution.

### 3. C++ → Java Comparison
*   **Sorting Arrays:**
    *   C++: `sort(arr, arr + n);`
    *   Java: `Arrays.sort(arr);`
*   **Sorting Lists:**
    *   C++: `sort(vec.begin(), vec.end());`
    *   Java: `Collections.sort(list);`
*   **Custom Sorting Comparator:**
    *   C++: Pass a bool comparison function: `sort(vec.begin(), vec.end(), cmp);`
    *   Java: Pass a custom Comparator interface (often using lambdas): `list.sort((a, b) -> a - b);`
*   **Limits Mapping:**
    *   C++ `INT_MAX` → Java `Integer.MAX_VALUE`
    *   C++ `INT_MIN` → Java `Integer.MIN_VALUE`
    *   C++ `LLONG_MAX` → Java `Long.MAX_VALUE`
    *   C++ `LLONG_MIN` → Java `Long.MIN_VALUE`

### 4. C++ Syntax/Example
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <climits>
#include <cmath>
using namespace std;

// Custom sort criteria
bool comparePairs(pair<int, int> a, pair<int, int> b) {
    return a.first < b.first;
}

int main() {
    int maxVal = INT_MAX;
    int minVal = INT_MIN;
    
    int minNum = min(5, 10);
    double power = pow(2, 3);
    
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
import java.util.Arrays;
import java.util.Collections;
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        int maxVal = Integer.MAX_VALUE;
        int minVal = Integer.MIN_VALUE;
        
        int minNum = Math.min(5, 10);
        double power = Math.pow(2, 3);
    }
}
```

### 6. Important Java Differences
*   **Primitive vs Object Custom Sorting:** You **cannot** use custom comparators with primitive arrays (e.g. `Arrays.sort(int[] arr, Comparator)` is invalid). Custom sorting only works with **Object arrays** (like `Integer[]` or custom classes) or lists (`ArrayList`).
*   **Comparator return structure:** A custom Comparator in Java returns:
    *   *Negative value:* If first argument is less than second (no swap).
    *   *Zero:* If they are equal.
    *   *Positive value:* If first argument is greater than second (swap).

### 7. Simple Hinglish Explanation
C++ mein hum custom sorting ke liye boolean comparator return kar dete the. Java mein hum `Comparator` functional interface ya **Lambda expressions** use karte hain. Java ka comparator `boolean` return nahi karta, balki ek integer return karta hai:
- Agar output negative (`< 0`) hai, toh sorting order switch nahi hoga.
- Agar output positive (`> 0`) hai, toh elements swap honge.
Yaad rakhna, custom sorting sirf wrapper objects par kaam karegi (jaise `Integer[]` ya `ArrayList<Integer>`), primitive arrays `int[]` par nahi!
Math functions ke liye hum `Math.min(a, b)` aur constants ke liye `Integer.MAX_VALUE` direct use karte hain.

### 8. Small Practical Examples
Let's see custom sorting using a 2D Array (representing a list of intervals: `[start, end]`). We want to sort intervals based on their start times.
```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[][] intervals = {
            {3, 5},
            {1, 9},
            {2, 4}
        };
        
        // Custom sort by the 1st element (index 0) of each pair
        Arrays.sort(intervals, (a, b) -> a[0] - b[0]);
        
        // Print sorted intervals
        for (int[] interval : intervals) {
            System.out.println(Arrays.toString(interval));
        }
        
        // Descending order sorting (requires Objects)
        Integer[] arr = {5, 2, 8, 1};
        Arrays.sort(arr, Collections.reverseOrder());
        System.out.println("Descending: " + Arrays.toString(arr));
    }
}
```

### 9. Expected Output
```text
[1, 9]
[2, 4]
[3, 5]
Descending: [8, 5, 2, 1]
```

### 10. Common Mistakes
*   **Integer Subtraction Overflow Trap:** In a custom comparator, writing `(a, b) -> a - b` works for positive numbers, but if `a` is a large positive value and `b` is negative, `a - b` can overflow the integer limit. The safe way is to use `Integer.compare(a, b)`.
    *Example:* `Arrays.sort(intervals, (a, b) -> Integer.compare(a[0], b[0]));`
*   **Attempting custom sort on primitive arrays:** `Arrays.sort(new int[]{4, 1, 3}, Collections.reverseOrder());` will fail to compile.

### 11. Interview Point
*   **What algorithm does `Arrays.sort()` use under the hood?**
    *   For **primitives** (like `int[]`), it uses **Dual-Pivot Quicksort** (which has \(O(N \log N)\) average performance but \(O(N^2)\) worst-case).
    *   For **objects** (like `Integer[]` or `String[]`), it uses **Timsort** (stable sort, guaranteed \(O(N \log N)\)).

### 12. Coding-Platform Usage
When checking limits (e.g. implementing path searches), always initialize your `max` target variable to `Integer.MIN_VALUE` and your `min` target variable to `Integer.MAX_VALUE`.
```java
int minCost = Integer.MAX_VALUE;
for (int cost : options) {
    minCost = Math.min(minCost, cost);
}
```

### 13. Quick Revision
*   Primitive sorting: `Arrays.sort(arr);`
*   List sorting: `Collections.sort(list);`
*   Descending sorting: `Arrays.sort(IntegerObjectArray, Collections.reverseOrder());`
*   Custom sorting (Lambda): `Arrays.sort(matrix, (a, b) -> Integer.compare(a[0], b[0]));`
*   Boundary checks: `Integer.MAX_VALUE`, `Integer.MIN_VALUE`, `Long.MAX_VALUE`, `Long.MIN_VALUE`.
*   Math helpers: `Math.abs()`, `Math.min()`, `Math.max()`, `Math.pow(base, exp)`.
