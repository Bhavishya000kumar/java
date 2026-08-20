# Chapter 1 — Java Basics

### 1. What is it?
Java is a class-based, object-oriented programming language. For competitive programming or placement tests, it runs on the Java Virtual Machine (JVM) which compiles code to bytecode and then interprets/JIT-compiles it.

### 2. Why do I need it for placements?
Many mass-hiring companies (Accenture, L&T, Capgemini, Cognizant) use platforms like Cocubes, Mettl, or AMCAT which offer C++ and Java. Knowing Java allows you to write, read, and debug code smoothly on these platforms when C++ is buggy or not available, or when Java is preferred.

### 3. C++ → Java Comparison
*   **Compilation:** C++ compiles directly to machine code (`.exe` or `.out`). Java compiles to bytecode (`.class`) via `javac`, which is executed by the JVM (`java`).
*   **Structure:** C++ allows global functions and variables. In Java, **everything** must reside inside a class.
*   **Main Method:** C++ uses a global `int main()` function. Java uses `public static void main(String[] args)` inside a class.

### 4. C++ Syntax/Example
```cpp
#include <iostream>
using namespace std;

int main() {
    cout << "Hello placements!" << endl;
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello placements!");
    }
}
```

### 6. Important Java Differences
*   **File Name Rule:** If a class is marked `public`, the file name **must** match the class name exactly (e.g., `Main.java` for `public class Main`).
*   **`static` main:** The main method must be `static` so that the JVM can call it without instantiating the class.
*   **No pointers:** Java does not have explicit pointers (like `int* ptr`). All object references are managed internally.

### 7. Simple Hinglish Explanation
C++ mein hum directly `int main()` likh kar kaam shuru kar dete the. Lekin Java mein har cheez ek Class ke andar honi chahiye. Java code ko run karne ke liye compile karke bytecode (`.class` file) banana padta hai jo JVM run karta hai. Mass-recruiter coding platforms par mostly class ka naam `Main` ya `Solution` hota hai, isliye hume `public class Main` ke andar hi `main` method likhna hota hai.

### 8. Small Practical Examples
```java
// Save this file as Main.java
public class Main {
    public static void main(String[] args) {
        // Output with newline
        System.out.println("Welcome to Java!");
        
        // Output without newline
        System.out.print("This is on ");
        System.out.print("the same line.");
    }
}
```

### 9. Expected Output
```text
Welcome to Java!
This is on the same line.
```

### 10. Common Mistakes
*   **Wrong File Name:** Saving the file as `main.java` (lowercase 'm') when the class is `public class Main` (uppercase 'M'). Java is case-sensitive!
*   **Missing `static`:** Writing `public void main(String[] args)` instead of `public static void main(String[] args)`. The program won't run.

### 11. Interview Point
*   **What is the difference between JDK, JRE, and JVM?**
    *   **JVM (Java Virtual Machine):** Executes the bytecode.
    *   **JRE (Java Runtime Environment):** JVM + Libraries required to run Java apps.
    *   **JDK (Java Development Kit):** JRE + Development tools (compiler `javac`, debugger, etc.).
*   **Why is the `main` method static?**
    Because the JVM needs to run the `main` method before any objects of the class are created.

### 12. Coding-Platform Usage
On LeetCode/Hackerrank:
*   You don't need to write the `main` method. You just write the method inside the solution class.
*   Example layout:
    ```java
    class Solution {
        public int add(int a, int b) {
            return a + b;
        }
    }
    ```

### 13. Quick Revision
*   Compile: `javac Main.java`
*   Run: `java Main`
*   Main entry: `public static void main(String[] args)`
*   Print: `System.out.println()`
