# Chapter 6 — Arrays ⭐⭐⭐

### 1. What is it?
An array is a collection of elements of the same data type stored at contiguous memory locations. In Java, arrays are dynamically allocated objects on the heap.

### 2. Why do I need it for placements?
Arrays form the bedrock of placement coding rounds. Most problems on platforms like LeetCode and HackerRank are based on arrays. Understanding how to create, manipulate, and sort arrays in Java is crucial.

### 3. C++ → Java Comparison
*   **Memory Allocation:** In C++, arrays can be allocated statically on the stack (`int arr[5];`). In Java, arrays are always allocated on the heap using the `new` keyword.
*   **Size Determination:**
    *   C++: `sizeof(arr)/sizeof(arr[0])` or `arr.size()` (for std::vector).
    *   Java: `arr.length` (a property, not a method).
*   **Declarations:**
    *   C++: `int arr[5];`
    *   Java: `int[] arr = new int[5];` (Standard style) or `int arr[] = new int[5];`.

### 4. C++ Syntax/Example
```cpp
#include <iostream>
#include <algorithm>
using namespace std;

int main() {
    int arr[5] = {5, 2, 8, 1, 9};
    int n = sizeof(arr) / sizeof(arr[0]);
    sort(arr, arr + n);
    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] arr = {5, 2, 8, 1, 9}; // Dynamic allocation under the hood
        int n = arr.length;
        Arrays.sort(arr);
        for (int i = 0; i < n; i++) {
            System.out.print(arr[i] + " ");
        }
    }
}
```

### 6. Important Java Differences
*   **Heap Allocation:** When you write `int[] arr = new int[5];`, the reference variable `arr` is stored on the stack, while the actual array of size 5 is allocated on the heap.
*   **No Pointer Arithmetic:** You cannot write `arr + 1` or `*(arr + i)`. Indexing is strictly done via `arr[i]`.
*   **Automatic Initialization:** Unlike C++ where stack arrays contain garbage values, Java arrays are automatically initialized to default values (`0` for `int`, `0.0` for `double`, `false` for `boolean`, `null` for objects).
*   **Out of Bounds Exception:** Accessing an index outside range throws `ArrayIndexOutOfBoundsException` at runtime instead of causing undefined behavior like C++.

### 7. Simple Hinglish Explanation
C++ mein hum `int arr[5]` likh kar garbage values ke sath memory allocate kar sakte the. Java mein aisa nahi hota. Java mein array humesha heap memory mein allocate hota hai aur initialize hote hi saare elements default values (`0`) se fill ho jaate hain. Array ka size nikalne ke liye hum `arr.length` likhte hain (bracket nahi lagate, yeh property hai function nahi).
Hum standard syntax `int[] arr` use karenge, jo C++ ke `int arr[]` se thoda alag hai par standard Java design hai.

### 8. Small Practical Examples
Let's see common utilities of the `Arrays` class.
```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] arr = {10, 5, 20, 15};
        
        // 1. Length
        System.out.println("Size: " + arr.length);
        
        // 2. Sorting
        Arrays.sort(arr);
        
        // 3. Printing array directly using Arrays utility
        System.out.println("Sorted Array: " + Arrays.toString(arr));
        
        // 4. Fill array
        int[] temp = new int[5];
        Arrays.fill(temp, -1);
        System.out.println("Filled Array: " + Arrays.toString(temp));
        
        // 5. Copying array
        int[] copied = Arrays.copyOf(arr, arr.length);
        System.out.println("Copied Array: " + Arrays.toString(copied));
    }
}
```

### 9. Expected Output
```text
Size: 4
Sorted Array: [5, 10, 15, 20]
Filled Array: [-1, -1, -1, -1, -1]
Copied Array: [5, 10, 15, 20]
```

### 10. Common Mistakes
*   **Calling length as function:** Writing `arr.length()` (with parentheses) instead of `arr.length`. (Strings use `length()`, arrays use `length`).
*   **Direct reference copy:** Writing `int[] b = a;` just copies the reference. Modifying `b[0]` modifies `a[0]`. To create a separate copy, use `Arrays.copyOf()` or `.clone()`.

### 11. Interview Point
*   **Where are arrays stored in Java?**
    All arrays in Java are dynamically allocated on the heap, regardless of whether they are declared inside a method or class.
*   **What is the enhanced for loop in Java?**
    It's equivalent to the range-based for loop in C++:
    ```java
    for (int num : arr) {
        System.out.print(num + " ");
    }
    ```

### 12. Coding-Platform Usage
Here are standard Java implementations of key algorithms:

#### Kadane's Algorithm Template (Max Subarray Sum)
```java
public int maxSubArray(int[] nums) {
    int maxSoFar = nums[0];
    int currentMax = nums[0];
    for (int i = 1; i < nums.length; i++) {
        currentMax = Math.max(nums[i], currentMax + nums[i]);
        maxSoFar = Math.max(maxSoFar, currentMax);
    }
    return maxSoFar;
}
```

#### Binary Search Template
```java
public int binarySearch(int[] nums, int target) {
    int low = 0, high = nums.length - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2; // Prevents overflow
        if (nums[mid] == target) return mid;
        else if (nums[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}
```

### 13. Quick Revision
*   Declare: `int[] arr = new int[size];`
*   Size: `arr.length`
*   Utilities: `Arrays.sort(arr)`, `Arrays.fill(arr, val)`, `Arrays.copyOf(arr, newLength)`, `Arrays.toString(arr)`.
*   Traversal: `for (int val : arr)`
*   Memory: Stack reference variable points to Heap object.
