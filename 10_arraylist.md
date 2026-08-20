# Chapter 10 — ArrayList ⭐⭐⭐

### 1. What is it?
An `ArrayList` is a resizable, dynamic array implementation of the `List` interface in Java. It can grow and shrink in size dynamically as elements are added or removed.

### 2. Why do I need it for placements?
In many DSA problems (e.g. Subarray Sum, Level Order Traversal of Binary Trees), the size of the output is not known beforehand. You must use `ArrayList` to collect elements and return them.

### 3. C++ → Java Comparison
*   **Containers Mapping:**
    *   C++: `vector<int> vec;`
    *   Java: `ArrayList<Integer> list = new ArrayList<>();`
*   **Wrapper Requirement:** C++ vectors can store primitive types (`vector<int>`). Java collection classes can **only store objects**. You cannot declare `ArrayList<int>`. You must use the wrapper class `ArrayList<Integer>`.
*   **Common Method Mapping:**

| C++ Vector | Java ArrayList |
|---|---|
| `vec.push_back(x)` | `list.add(x)` |
| `vec[i]` | `list.get(i)` |
| `vec[i] = val` | `list.set(i, val)` |
| `vec.size()` | `list.size()` |
| `vec.clear()` | `list.clear()` |
| `vec.erase(vec.begin() + i)` | `list.remove(i)` |

### 4. C++ Syntax/Example
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    vector<int> vec;
    vec.push_back(10);
    vec.push_back(5);
    sort(vec.begin(), vec.end());
    
    cout << vec[0] << " Size: " << vec.size() << endl;
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
import java.util.ArrayList;
import java.util.Collections;

public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        list.add(10);
        list.add(5);
        Collections.sort(list); // Sorting ArrayList
        
        System.out.println(list.get(0) + " Size: " + list.size());
    }
}
```

### 6. Important Java Differences
*   **Primitives vs Wrappers:** Java has primitive types (`int`, `char`, `double`) and their corresponding Object classes called wrapper classes (`Integer`, `Character`, `Double`).
*   **Autoboxing and Unboxing:** Java automatically converts between primitive types and their wrapper objects.
    *   *Autoboxing:* Converting `int` to `Integer` automatically (e.g., `list.add(5)` converts primitive `5` to `Integer.valueOf(5)`).
    *   *Unboxing:* Converting `Integer` back to `int` automatically (e.g., `int x = list.get(0)`).
*   **Index-based Removal vs Value-based Removal:**
    *   `list.remove(1)` removes the element at index 1.
    *   `list.remove(Integer.valueOf(1))` removes the actual object with value 1.

### 7. Simple Hinglish Explanation
C++ mein hum `vector<int>` banate the jismein automatic size adjust ho jata tha. Java mein wahi kaam `ArrayList` karta hai.
Sabse badi baat yeh hai ki Java Collections mein hum direct primitives (`int`, `char`) nahi daal sakte. Hume classes use karni padti hain jinhe **Wrapper Classes** bolte hain. Jaise `int` ke liye `Integer`, `char` ke liye `Character`.
Values insert karne ke liye `add(val)` use karenge, element read karne ke liye `get(index)` aur value update karne ke liye `set(index, val)`. Sort karne ke liye `Collections.sort(list)` use karenge.

### 8. Small Practical Examples
Let's see common `ArrayList` operations:
```java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        
        // 1. Add elements
        list.add(10);
        list.add(20);
        list.add(30);
        
        // 2. Size
        System.out.println("Size: " + list.size());
        
        // 3. Get element at index
        System.out.println("Element at 1: " + list.get(1)); // 20
        
        // 4. Update element
        list.set(1, 99);
        System.out.println("Updated element at 1: " + list.get(1)); // 99
        
        // 5. Check if element exists
        System.out.println("Contains 30: " + list.contains(30)); // true
        
        // 6. Remove index
        list.remove(0); // Removes 10
        System.out.println("After removing index 0: " + list);
    }
}
```

### 9. Expected Output
```text
Size: 3
Element at 1: 20
Updated element at 1: 99
Contains 30: true
After removing index 0: [99, 30]
```

### 10. Common Mistakes
*   **Declaring with primitives:** Writing `ArrayList<int> list = new ArrayList<>();` will result in a compiler error. Always write `ArrayList<Integer>`.
*   **Confusing `.size()` and `.length`:** For arrays, it is `.length` (property). For ArrayList, it is `.size()` (method). For Strings, it is `.length()` (method).
*   **Comparing wrappers with `==`:** If you check `list.get(i) == list.get(j)`, it compares reference addresses. For values outside range -128 to 127, this might evaluate to `false` even if the numbers are equal. **Always use `.equals()` or unbox them explicitly** (`(int)list.get(i) == (int)list.get(j)`).

### 11. Interview Point
*   **What is the difference between Array and ArrayList?**
    *   Array is of fixed size, can store primitives, and uses `[]` for access.
    *   ArrayList is dynamic, can only store objects (wrapper classes), and uses methods (`add()`, `get()`) for access.
*   **What is Autoboxing and Unboxing?**
    Automatic conversion of primitive types to wrapper class objects and vice-versa.

### 12. Coding-Platform Usage
Converting an `ArrayList<Integer>` back to a primitive array `int[]` is a common requirement in platform outputs:
```java
// Option 1: Iterating manually
int[] result = new int[list.size()];
for (int i = 0; i < list.size(); i++) {
    result[i] = list.get(i);
}

// Option 2: Using streams (useful but manual is faster in coding assessments)
int[] res = list.stream().mapToInt(i -> i).toArray();
```

### 13. Quick Revision
*   Creation: `ArrayList<Integer> list = new ArrayList<>();`
*   Add: `list.add(val)`. Read: `list.get(index)`. Modify: `list.set(index, val)`.
*   Size: `list.size()`. Remove: `list.remove(index)`.
*   Sorting: `Collections.sort(list)`.
*   Never write `ArrayList<int>`. Always use `ArrayList<Integer>`.
