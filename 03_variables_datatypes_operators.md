# Chapter 3 — Variables, Data Types & Operators

### 1. What is it?
Variables are container names storing data values. Data types specify the size and type of values that can be stored. Operators are symbols used to perform operations on variables and values.

### 2. Why do I need it for placements?
Mass-hiring platforms present math and array problems where variables can overflow (exceeding standard limits). If you use `int` instead of `long` for large results, your tests will fail. Knowing primitive limits is crucial for logic correctness.

### 3. C++ → Java Comparison
*   **Variable Sizes:** In C++, sizes are platform-dependent (e.g., `int` could be 16-bit or 32-bit). In Java, data type sizes are **strictly fixed** and platform-independent.
*   **Data Type Mapping:**
    *   C++ `int` (usually 4 bytes) → Java `int` (always 4 bytes, signed).
    *   C++ `long long` (8 bytes) → Java `long` (always 8 bytes, signed).
    *   C++ `bool` (1 byte) → Java `boolean` (cannot be cast to int, only `true`/`false`).
    *   C++ `char` (1 byte ASCII) → Java `char` (2 bytes, supports Unicode/UTF-16).

### 4. C++ Syntax/Example
```cpp
#include <iostream>
using namespace std;

int main() {
    int a = 10;
    long long b = 100000000000LL;
    bool flag = true;
    char ch = 'A';
    
    // Explicit casting
    int ch_val = (int)ch;
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
public class Main {
    public static void main(String[] args) {
        int a = 10;
        long b = 100000000000L; // Note the 'L' suffix
        boolean flag = true;
        char ch = 'A';
        
        // Explicit casting
        int chVal = (int) ch;
    }
}
```

### 6. Important Java Differences
*   **No Unsigned Primitives:** Java does not have `unsigned int` or `unsigned long`. All numeric types are signed.
*   **Char Size:** Java's `char` is 2 bytes (16-bit) to support international Unicode characters, whereas C++ uses 1 byte ASCII `char`.
*   **Boolean is strict:** In C++, a non-zero integer is treated as `true` (e.g., `if (1)` compiles). In Java, `boolean` is a separate type. You **cannot** do `if (1)`. You must write `if (1 != 0)` or `if (true)`.
*   **Float Suffix:** In Java, you must write `float f = 5.5f;` because decimal literals are default `double` in Java. If you write `float f = 5.5;`, the compiler throws an error.

### 7. Simple Hinglish Explanation
C++ mein `long long` variable 8-bytes ka hota tha. Java mein wahi kaam `long` variable karta hai. Yaad rakhna ki Java mein long variable assign karte time value ke end mein `L` ya `l` lagana zaroori hai (jaise: `100000000000L`), warna compiler use `int` samajh kar compile error de dega.
Sabse bada difference `boolean` ka hai: Java mein `if (5)` ya `if (1)` error dega. Aapko strictly boolean expression hi loops ya conditions mein likhna padega.

### 8. Small Practical Examples
```java
public class Main {
    public static void main(String[] args) {
        // Integer division vs double division
        int x = 5;
        int y = 2;
        System.out.println("Int div: " + (x / y)); // Outputs 2
        System.out.println("Double div: " + ((double) x / y)); // Outputs 2.5
        
        // Overflow demonstration
        int maxVal = Integer.MAX_VALUE; // 2147483647
        System.out.println("Max Int: " + maxVal);
        System.out.println("Overflowed: " + (maxVal + 1)); // Cycles to negative
        
        // Logical check
        boolean cond1 = true;
        boolean cond2 = false;
        System.out.println("AND: " + (cond1 && cond2));
        
        // Ternary operator
        int result = (x > y) ? x : y;
        System.out.println("Ternary output: " + result);
    }
}
```

### 9. Expected Output
```text
Int div: 2
Double div: 2.5
Max Int: 2147483647
Overflowed: -2147483648
AND: false
Ternary output: 5
```

### 10. Common Mistakes
*   **Missing 'L' suffix for long:** `long value = 9999999999;` fails because the number is out of bounds for default `int`. Correct way: `long value = 9999999999L;`.
*   **Assigning double to float:** `float f = 3.14;` gives compiler error. Correct way: `float f = 3.14f;`.
*   **Wrong conversion to char:** Attempting to assign negative values directly to char without casting.

### 11. Interview Point
*   **Why does Java not support unsigned integers?**
    Java's creators wanted to simplify the language by reducing common errors related to unsigned math and sign expansion.
*   **What is standard wrapper class size limit?**
    `Integer.MAX_VALUE` is \(2^{31} - 1\), and `Long.MAX_VALUE` is \(2^{63} - 1\).

### 12. Coding-Platform Usage
In coding rounds (e.g., LeetCode), if constraints mention \(N \le 10^9\), operations like sum or multiplication may exceed the integer limit (\(2 \times 10^9\)). Always store such intermediate results in `long` variable types rather than `int`.

### 13. Quick Revision
*   Guaranteed sizes: `int` = 32-bit, `long` = 64-bit, `char` = 16-bit.
*   Float requires suffix: `float f = 1.0f;`.
*   Long requires suffix: `long l = 100000000000L;`.
*   Strict boolean: No integer representation for conditions (e.g., `if (1)` is invalid).
