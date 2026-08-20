# Chapter 9 — StringBuilder ⭐⭐⭐

### 1. What is it?
`StringBuilder` is a mutable sequence of characters. Unlike `String`, it allows modifying characters and appending content in-place without creating new objects in memory.

### 2. Why do I need it for placements?
In coding rounds, appending characters to a `String` inside a loop runs in \(O(N^2)\) time because a new String object is allocated at each iteration. Using `StringBuilder` optimizes string building loops to \(O(N)\) time, preventing TLE.

### 3. C++ → Java Comparison
*   **Concatenation in Loops:**
    *   C++: `s += ch` (Modifies the existing string capacity dynamically; \(O(1)\) amortized).
    *   Java String: `s = s + ch` (Allocates a new String object, copies all characters; \(O(N)\) time per step).
    *   Java StringBuilder: `sb.append(ch)` (Modifies internal character array dynamically; \(O(1)\) amortized, equivalent to C++).

### 4. C++ Syntax/Example
```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string s = "";
    for(int i = 0; i < 5; i++) {
        s += to_string(i); // Efficient in C++
    }
    s[2] = 'X'; // In-place change
    reverse(s.begin(), s.end());
    cout << s;
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
public class Main {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < 5; i++) {
            sb.append(i); // Efficient O(1) appending
        }
        sb.setCharAt(2, 'X'); // In-place modification
        sb.reverse(); // Reverse in-place
        
        String result = sb.toString(); // Convert back to String
        System.out.println(result);
    }
}
```

### 6. Important Java Differences
*   **StringBuilder is NOT a String:** You cannot assign a `StringBuilder` to a `String` variable directly. You must call `.toString()` to get a standard `String` representation.
*   **No thread safety:** `StringBuilder` is not thread-safe. (Java also has `StringBuffer` which is thread-safe, but because of lock overhead, it is slower. Always use `StringBuilder` in coding rounds).

### 7. Simple Hinglish Explanation
Java mein agar aap `for` loop chala kar string mein characters jode jaaoge (jaise: `s = s + ch`), toh har baar poori string copy hogi. Agar loop 10,000 baar chala, toh performance bohot slow ho jayegi aur online round mein **Time Limit Exceeded (TLE)** aa jayega.
Isko solve karne ke liye Java mein `StringBuilder` hota hai. Yeh bilkul C++ string ki tarah behave karta hai jo in-place modification allow karta hai. `append()`, `insert()`, `deleteCharAt()`, `reverse()` jaise helpful functions ismein pehle se hote hain. Final string return karne se pehle hum bas `.toString()` call kar lete hain.

### 8. Small Practical Examples
Let's see some basic mutation techniques:
```java
public class Main {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("placement");
        
        // 1. Append
        sb.append("2026");
        System.out.println("Append: " + sb); // "placement2026"
        
        // 2. Insert at index
        sb.insert(0, "Java_");
        System.out.println("Insert: " + sb); // "Java_placement2026"
        
        // 3. Delete characters (start index, end index - exclusive)
        sb.delete(0, 5);
        System.out.println("Delete: " + sb); // "placement2026"
        
        // 4. Delete character at index
        sb.deleteCharAt(sb.length() - 1);
        System.out.println("Delete char: " + sb); // "placement202"
        
        // 5. Replace character
        sb.setCharAt(0, 'P');
        System.out.println("Set char: " + sb); // "Placement202"
    }
}
```

### 9. Expected Output
```text
Append: placement2026
Insert: Java_placement2026
Delete: placement2026
Delete char: placement202
Set char: Placement202
```

### 10. Common Mistakes
*   **Comparing StringBuilder using `.equals()`:** `StringBuilder` does not override `equals()`. Calling `sb1.equals(sb2)` does reference comparison, not value comparison. To compare values, do `sb1.toString().equals(sb2.toString())`.
*   **Using `+` instead of `.append()`:** Writing `sb.append(a + b)` inside a loop defeats the purpose by creating temporary strings. Write `sb.append(a).append(b)` instead.

### 11. Interview Point
*   **What is the difference between String, StringBuilder, and StringBuffer?**
    *   `String`: Immutable, slow concatenation, thread-safe.
    *   `StringBuilder`: Mutable, fast concatenation, not thread-safe (preferred for single-threaded DSA coding).
    *   `StringBuffer`: Mutable, thread-safe (synchronized methods), slower than `StringBuilder`.

### 12. Coding-Platform Usage
When constructing responses in problems like "String Compression" or "Reverse Words in a String", always use `StringBuilder` as the workspace container. Here is how you can use it to build a reversed string of space-separated words:
```java
public String reverseWords(String s) {
    String[] words = s.trim().split("\\s+");
    StringBuilder sb = new StringBuilder();
    for (int i = words.length - 1; i >= 0; i--) {
        sb.append(words[i]);
        if (i > 0) sb.append(" ");
    }
    return sb.toString();
}
```

### 13. Quick Revision
*   Creation: `StringBuilder sb = new StringBuilder();`
*   Adding data: `sb.append(val);` (can append ints, chars, strings).
*   Mutation: `sb.setCharAt(index, ch)`, `sb.deleteCharAt(index)`.
*   Reversing: `sb.reverse()`.
*   Convert to String: `sb.toString()`.
