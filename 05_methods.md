# Chapter 5 — Methods

### 1. What is it?
A method is a block of code (similar to a function in C++) that runs only when called. Data is passed to methods as parameters, and they can return value outputs.

### 2. Why do I need it for placements?
In online assessments (LeetCode/AMCAT/Cocubes), you do not write the driver code. You are given a class and must write/complete a specific method (e.g., `public int solve(int[] nums)`). Understanding parameters, static functions, and memory models is vital.

### 3. C++ → Java Comparison
*   **Terminology:** C++ has standalone "functions". Since Java is purely object-oriented, all functions exist inside classes and are called "methods".
*   **Static vs Non-static:** Standalone helper methods in Java are declared `static` (similar to static functions in C++), meaning they can be invoked without creating an instance of the containing class.
*   **Parameters Passing:**
    *   C++: Supports pass-by-value (`void func(int x)`) and pass-by-reference (`void func(int &x)`).
    *   Java: **Strictly pass-by-value**. There is **no** pass-by-reference (`&`) operator in Java.

### 4. C++ Syntax/Example
```cpp
#include <iostream>
using namespace std;

// Pass by reference allowed
void updateValue(int &num) {
    num = 20;
}

int main() {
    int val = 10;
    updateValue(val);
    cout << val; // Output is 20
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
public class Main {
    // Pass by value only
    public static void updateValue(int num) {
        num = 20; // Does not affect the original variable
    }

    public static void main(String[] args) {
        int val = 10;
        updateValue(val);
        System.out.println(val); // Output is still 10
    }
}
```

### 6. Important Java Differences
*   **Strict Pass-By-Value:** For primitives (`int`, `char`, `double`, etc.), Java passes a copy of the actual value. For objects (arrays, lists, maps), Java passes a copy of the **reference** (the address) of the object by value.
*   This means:
    1.  If you change the reference to a new object inside a method, the change is **not** reflected in the caller.
    2.  If you modify the contents (like changing `arr[0] = 99`), the change **is** visible in the caller because both references point to the same object on the heap.

### 7. Simple Hinglish Explanation
C++ mein agar hum chahte the ki function original variable ko change kare, toh hum ampersand (`&`) lagakar pass-by-reference karte the.
**Java mein pass-by-reference jaisa kuch nahi hota.** Java humesha pass-by-value karta hai.
- Primitives (`int`, `char`) pass hote hain toh unki copy banti hai. Original values safe rehti hain.
- Objects (jaise array ya class objects) pass hote hain, toh unke reference (address) ki copy pass hoti hai. Agar aap method ke andar array ke data ko update karoge (jaise `arr[i] = x`), toh original array change **hoga**. Lekin agar aap method mein reference badalne ki koshish karoge (jaise `arr = new int[5]`), toh original caller array par koi farq nahi padega.

### 8. Small Practical Examples
Let's see what happens when we modify objects inside a method vs primitives.
```java
public class Main {
    public static void modifyPrimitives(int x) {
        x = 50;
    }

    public static void modifyArray(int[] arr) {
        arr[0] = 99; // Modifies the actual array element
    }

    public static void reassignArray(int[] arr) {
        arr = new int[]{1, 2, 3}; // Points to a new memory, caller won't see this
    }

    public static void main(String[] args) {
        int n = 10;
        modifyPrimitives(n);
        System.out.println("Primitive after modify: " + n); // 10

        int[] myArray = {10, 20, 30};
        modifyArray(myArray);
        System.out.println("Array[0] after modify: " + myArray[0]); // 99

        reassignArray(myArray);
        System.out.println("Array[0] after reassign: " + myArray[0]); // Still 99
    }
}
```

### 9. Expected Output
```text
Primitive after modify: 10
Array[0] after modify: 99
Array[0] after reassign: 99
```

### 10. Common Mistakes
*   **Expecting primitive changes to reflect:** Trying to swap two integer values using a helper method. In Java, this cannot be done by passing primitives directly.
*   **Calling non-static methods from static main:**
    ```java
    public class Main {
        void hello() { System.out.println("Hello"); }
        public static void main(String[] args) {
            hello(); // Compiler error! Cannot make a static reference to non-static method
        }
    }
    ```
    *Fix:* Make `hello()` `static` or instantiate the class.

### 11. Interview Point
*   **Is Java pass-by-value or pass-by-reference?**
    Java is **strictly pass-by-value**. People often get confused because passing an object reference allows mutating the object, but we are passing the object reference *by value* (the memory address value is copied).

### 12. Coding-Platform Usage
When solving problems recursively (like backtracking or DFS), you often pass a helper array/list to track path history. Because Java passes the array reference by value, modifying the list in any recursive branch will affect other branches. You must manually undo changes (backtrack) or create new copies when passing data.

### 13. Quick Revision
*   Java has no `&` reference operator for parameter passing.
*   Primitives are passed by copy; original values remain unchanged.
*   Objects/Arrays are passed by reference-value; elements can be mutated, but the reference itself cannot be reassigned.
*   Non-static methods cannot be called directly from static contexts.
