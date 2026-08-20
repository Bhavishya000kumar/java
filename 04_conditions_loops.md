# Chapter 4 — Conditions & Loops

### 1. What is it?
Conditionals (`if`, `else`, `switch`) control program flow based on boolean outcomes. Loops (`for`, `while`, `do-while`) repeat code execution blocks.

### 2. Why do I need it for placements?
Almost every placement programming question requires array traversals or checking conditions. Mastering loop controls (`break`, `continue`) is fundamental to solving problems correctly.

### 3. C++ → Java Comparison
The core syntax of loops and conditions in Java is identical to C++. The only major divergence is that Java demands **strict boolean expressions** for checks.
*   **Condition Check:**
    *   C++: `if (x)` (compiles if `x != 0`)
    *   Java: `if (x != 0)` (strict boolean required)
*   **Switch Expression:**
    *   C++: Supports integer-like types and characters.
    *   Java: Supports primitives (except `float`/`double`), wrapper classes, strings (`String`), and enums.

### 4. C++ Syntax/Example
```cpp
#include <iostream>
using namespace std;

int main() {
    int x = 5;
    if (x) { // Compiles in C++
        cout << "Non-zero" << endl;
    }
    
    for (int i = 0; i < 5; i++) {
        if (i == 2) continue;
        cout << i << " ";
    }
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
public class Main {
    public static void main(String[] args) {
        int x = 5;
        if (x != 0) { // Must be a boolean expression
            System.out.println("Non-zero");
        }
        
        for (int i = 0; i < 5; i++) {
            if (i == 2) continue;
            System.out.print(i + " ");
        }
    }
}
```

### 6. Important Java Differences
*   **Condition Type:** Expressions like `if (a = b)` will throw a compile error in Java if `a` and `b` are not booleans (in C++, it evaluates to the value of `a`).
*   **Switch with String:** Java allows using strings in switch statements (since Java 7), which is not natively supported in standard C++.
    ```java
    String role = "Admin";
    switch(role) {
        case "Admin": System.out.println("Full Access"); break;
        default: System.out.println("Limited Access");
    }
    ```

### 7. Simple Hinglish Explanation
Java mein conditions aur loops likhne ka tareeka bilkul C++ jaisa hi hai. `if`, `for`, `while` sab same dikhte hain. Bas ek baat dhyan rakhni hai ki C++ mein hum loop ko rokne ya check karne ke liye `while(1)` likh dete the, par Java mein `while(1)` error dega—aapko `while(true)` likhna padega. Break aur continue statements bhi C++ ki tarah hi behave karti hain.

### 8. Small Practical Examples
Let's see standard loop iterations and control structures.
```java
public class Main {
    public static void main(String[] args) {
        // While loop
        int count = 1;
        while (count <= 3) {
            System.out.println("Count: " + count);
            count++;
        }
        
        // Do-while loop
        int val = 10;
        do {
            System.out.println("Runs at least once even if condition fails.");
        } while (val < 5);
    }
}
```

### 9. Expected Output
```text
Count: 1
Count: 2
Count: 3
Runs at least once even if condition fails.
```

### 10. Common Mistakes
*   **Using integer in conditions:** `while(n--)` inside Java is a compile-time error. Write `while(n > 0) { n--; }` instead.
*   **Forgetting break in switch:** Missing a `break` causes execution to fall through to the next case (same as C++).

### 11. Interview Point
*   **Can we use `String` inside a switch statement in Java?**
    Yes, Java supports Strings in switch cases since Java 7. Under the hood, it compares the hash code of the string.
*   **What are labeled break and continue in Java?**
    Unlike C++, Java doesn't have `goto`. However, it supports labeled loops to break out of nested outer loops:
    ```java
    outer:
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            if (i == 1 && j == 1) break outer; // breaks the outer loop
        }
    }
    ```

### 12. Coding-Platform Usage
When implementing nested loops for algorithms like searching in 2D grids, labeled breaks can be very useful to immediately terminate outer loops instead of using temporary flag variables.

### 13. Quick Revision
*   If-else, switch, for, while, do-while syntax is identical to C++.
*   No `if (1)` or `while (1)` allowed. Use `if (true)` or `while (true)`.
*   Java switch allows checking String values.
*   Java supports labeled break/continue (`break labelName;`).
