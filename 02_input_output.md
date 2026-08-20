# Chapter 2 — Input / Output

### 1. What is it?
Input/Output (I/O) refers to reading data from standard input (keyboard/console) and writing data to standard output (console). In Java, this is primarily done using the `Scanner` class for basic needs and `BufferedReader` for fast operations.

### 2. Why do I need it for placements?
Mass-recruitment platforms (Accenture, Capgemini, etc.) often require you to read variables, arrays, and strings from console input and print results in a specific format. Incorrectly handling newlines or using slow I/O can lead to code failures or Time Limit Exceeded (TLE) errors.

### 3. C++ → Java Comparison
*   **Standard Input:**
    *   C++: `cin >> x;`
    *   Java: `Scanner sc = new Scanner(System.in); int x = sc.nextInt();`
*   **String/Line Input:**
    *   C++: `getline(cin, s);`
    *   Java: `String s = sc.nextLine();`
*   **Standard Output:**
    *   C++: `cout << x << "\n";`
    *   Java: `System.out.println(x);`

### 4. C++ Syntax/Example
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    int age;
    string name;
    cin >> age;
    cin.ignore(); // Clear buffer
    getline(cin, name);
    cout << "Age: " << age << ", Name: " << name << endl;
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int age = sc.nextInt();
        sc.nextLine(); // Clear buffer / consume leftover newline
        String name = sc.nextLine();
        System.out.println("Age: " + age + ", Name: " + name);
    }
}
```

### 6. Important Java Differences
*   **Scanner Tokenization:** `sc.next()` reads a single word (stops at space). `sc.nextLine()` reads the entire line (stops at newline).
*   **The Leftover Newline Trap:** When you read an integer using `sc.nextInt()`, it leaves the `\n` character in the buffer. If you immediately call `sc.nextLine()`, it reads this empty newline instead of your actual string. You must consume the leftover newline using an extra `sc.nextLine()` call first.

### 7. Simple Hinglish Explanation
C++ mein jab hum `cin >> x` karte hain aur uske baad `getline(cin, s)` karte hain, toh hume `cin.ignore()` likhna padta hai buffer clear karne ke liye. Bilkul wahi issue Java mein bhi hota hai. Jab aap `sc.nextInt()` use karte ho, toh input buffer mein ek newline `\n` bacha reh jata hai. Uske theek baad agar `sc.nextLine()` call karoge, toh woh bina input liye empty string read kar lega. Isko solve karne ke liye beech mein ek extra `sc.nextLine()` call karke buffer clear kiya jata hai.

### 8. Small Practical Examples
Let's see a complete program reading different types of values.
```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        
        System.out.print("Enter an integer: ");
        int num = sc.nextInt();
        
        System.out.print("Enter a double: ");
        double d = sc.nextDouble();
        
        // Consume newline character left behind
        sc.nextLine();
        
        System.out.print("Enter a full line: ");
        String str = sc.nextLine();
        
        System.out.println("Num: " + num + ", Double: " + d + ", Line: " + str);
    }
}
```

### 9. Expected Output
```text
Enter an integer: 10
Enter a double: 5.5
Enter a full line: Hello Placement
Num: 10, Double: 5.5, Line: Hello Placement
```

### 10. Common Mistakes
*   **Forgetting to import Scanner:** Always add `import java.util.Scanner;` at the top of the file.
*   **Falling into the Newline Trap:** Getting empty values for strings because of consecutive `nextInt()` / `nextLine()` calls.

### 11. Interview Point
*   **Why is `Scanner` slow, and what is the alternative for large inputs?**
    `Scanner` parses the input using regular expressions, making it slow for reading large amounts of data. The faster alternative is `BufferedReader` combined with `StringTokenizer`.
    ```java
    import java.io.BufferedReader;
    import java.io.InputStreamReader;
    import java.io.IOException;
    import java.util.StringTokenizer;

    public class FastIO {
        public static void main(String[] args) throws IOException {
            BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
            StringTokenizer st = new StringTokenizer(br.readLine());
            int n = Integer.parseInt(st.nextToken());
        }
    }
    ```

### 12. Coding-Platform Usage
*   In HackerRank/GeeksforGeeks, you might need to write the template for reading inputs. Use `Scanner` as it is simple and sufficient for 95% of mass-recruitment coding tests.
*   In LeetCode, you don't write I/O. The inputs are passed directly as parameters to your solution methods.

### 13. Quick Revision
*   Import: `import java.util.Scanner;`
*   Create: `Scanner sc = new Scanner(System.in);`
*   Methods: `sc.nextInt()`, `sc.nextDouble()`, `sc.next()` (word), `sc.nextLine()` (line).
*   Trap: Empty string read after `nextInt()`. Resolve by adding an intermediate `sc.nextLine()`.
