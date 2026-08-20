# Chapter 8 — Strings ⭐⭐⭐

### 1. What is it?
A String is a sequence of characters. In Java, Strings are objects of the `String` class. They are **immutable**, meaning once created, their values cannot be changed in memory.

### 2. Why do I need it for placements?
String parsing and manipulation are heavily tested in coding interviews. Knowing how to extract substrings, split strings by delimiters, and check equality is essential for mass-recruiter test formats.

### 3. C++ → Java Comparison
*   **Mutability:** C++ strings are mutable (`s[0] = 'a'` modifies the string). Java Strings are immutable; any change creates a **new** String object.
*   **Character Access:**
    *   C++: `char ch = s[i];`
    *   Java: `char ch = s.charAt(i);` (direct square bracket syntax is not allowed).
*   **Length:**
    *   C++: `s.length()` or `s.size()`.
    *   Java: `s.length()` (method with parentheses).
*   **Comparison:**
    *   C++: `s == t` compares the characters inside the strings.
    *   Java: `s.equals(t)` compares characters. `s == t` checks if both reference variables point to the same memory object (reference comparison).

### 4. C++ Syntax/Example
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s = "hello";
    s[0] = 'H'; // Mutable
    if (s == "Hello") {
        cout << "Equal!" << endl;
    }
    cout << s.length() << endl;
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
public class Main {
    public static void main(String[] args) {
        String s = "hello";
        // s.charAt(0) = 'H'; // Compiler error! Immutable.
        
        // Correct way to modify: Create new string
        s = "H" + s.substring(1); 
        
        if (s.equals("Hello")) { // String content comparison
            System.out.println("Equal!");
        }
        System.out.println(s.length());
    }
}
```

### 6. Important Java Differences
*   **String Pool:** Java saves memory by using a "String Constant Pool" (SCP). When you create a literal `String s = "abc";`, Java checks the pool first. If "abc" exists, it reuses the reference. If you use `new String("abc")`, it bypasses the pool and creates a new object in the heap.
*   **Trap: Comparing with `==`**
    ```java
    String s1 = "hello";
    String s2 = "hello";
    String s3 = new String("hello");
    System.out.println(s1 == s2); // true (both point to same SCP reference)
    System.out.println(s1 == s3); // false (s3 points to a heap object)
    System.out.println(s1.equals(s3)); // true (compares values)
    ```
*   **Substring Syntax:** `s.substring(start, end)` returns character indexes from `start` to `end - 1`. The index `end` is **exclusive**.

### 7. Simple Hinglish Explanation
C++ mein string mutable hoti hai, matlab hum `s[i] = 'a'` likh kar characters change kar sakte hain. Java mein string **immutable** hoti hai. Agar aapne ek baar string bana di, toh memory mein change nahi ho sakti. Agar aap use change karne ki koshish karoge toh Java background mein ek naya string object bana deta hai.
Java mein character nikalne ke liye hum strictly `s.charAt(i)` use karenge. Aur do strings ke characters compare karne ke liye `s.equals(t)` use karenge. `==` se address compare hote hain, content nahi!

### 8. Small Practical Examples
Let's see common String functions used in coding tests:
```java
public class Main {
    public static void main(String[] args) {
        String s = "Placement Coding Course";
        
        // 1. Substring (index 0 to 8)
        System.out.println("Substring: " + s.substring(0, 9)); // "Placement"
        
        // 2. Contains
        System.out.println("Contains: " + s.contains("Coding")); // true
        
        // 3. Index of character
        System.out.println("Index of 'C': " + s.indexOf('C')); // 10
        
        // 4. Split by spaces
        String[] words = s.split(" ");
        for (String word : words) {
            System.out.println("Word: " + word);
        }
        
        // 5. Trim (remove leading/trailing spaces)
        String messy = "   hello space   ";
        System.out.println("Trimmed: '" + messy.trim() + "'");
    }
}
```

### 9. Expected Output
```text
Substring: Placement
Contains: true
Index of 'C': 10
Word: Placement
Word: Coding
Word: Course
Trimmed: 'hello space'
```

### 10. Common Mistakes
*   **Using `==` to compare input strings:** User inputs checked using `==` will almost always evaluate to `false` because they are allocated dynamically in heap. Always use `.equals()`.
*   **Index out of bounds on substring:** Passing parameters `s.substring(0, s.length() + 1)` throws `StringIndexOutOfBoundsException`.

### 11. Interview Point
*   **Why are Strings immutable in Java?**
    1.  **Security:** Strings are used for parameters like database URLs, network connections, usernames. Immutability stops hackers from changing them.
    2.  **String Pool:** Reusing String objects would not be possible if they were mutable (changing one reference would change all others).
    3.  **Thread safety:** Immutable objects are naturally thread-safe.

### 12. Coding-Platform Usage
Converting numeric values to String and vice-versa:
*   Int to String: `String s = String.valueOf(num);` or `Integer.toString(num);` or simple concatenation `s = num + "";`.
*   String to Int: `int num = Integer.parseInt(s);`.

### 13. Quick Revision
*   String content check: `s.equals(t)`. Case-insensitive: `s.equalsIgnoreCase(t)`.
*   Get character: `s.charAt(i)`.
*   Size: `s.length()`.
*   Substring: `s.substring(start, end)` (excluding `end`).
*   Immutable: Changing a String creates a new object.
