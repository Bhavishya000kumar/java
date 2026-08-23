# 100 Java Placement Interview Questions

This document contains exactly 100 high-yield Java interview questions categorized to target placement tests and interviews (Accenture, Cognizant, Capgemini, L&T, etc.).

---

## 📂 Section 1: Java Fundamentals (Q1 - Q25)

#### Q1: What is the difference between JDK, JRE, and JVM?
*   **Answer:** JVM runs the bytecode. JRE contains JVM and runtime libraries. JDK is JRE plus development tools (like compiler `javac`).
*   **Hinglish:** JVM program chalata hai, JRE running environment deta hai, aur JDK compiler aur tools ke sath development package hai.
*   **Point:** JVM is platform-dependent, but bytecode is platform-independent.
*   **Trap:** Don't say JDK is enough to run programs without JRE; JDK contains JRE.

#### Q2: Why is Java platform-independent?
*   **Answer:** Because Java compiles code into intermediate bytecode (`.class`), which can run on any system with a JVM installed.
*   **Hinglish:** Code compile hoke bytecode banta hai, jo har OS pe standard rehta hai. JVM use system machine code mein badalta hai.
*   **Point:** "Write Once, Run Anywhere" (WORA).

#### Q3: Why is Java not purely object-oriented?
*   **Answer:** Java supports primitive data types like `int`, `char`, `double`, which are not objects.
*   **Hinglish:** Java mein primitives objects nahi hote, isliye yeh pure OOP language nahi hai.
*   **Point:** Wrapper classes can be used to make it appear pure.

#### Q4: What is the difference between compiler and interpreter in Java?
*   **Answer:** `javac` compiles code into bytecode. During execution, JVM's interpreter reads bytecode line-by-line, and the JIT compiler compiles hotspots to native code.
*   **Hinglish:** `javac` pehle bytecode banata hai. Execution ke time JVM bytecode ko interpret karta hai.

#### Q5: Can we run a Java program without the `main` method?
*   **Answer:** No. From Java 7 onwards, the `main` method is strictly required to start execution.
*   **Hinglish:** Java 7 se pehle static block se run ho jata tha, par ab `main` method mandatory hai.

#### Q6: Why is the `main` method static?
*   **Answer:** So the JVM can call the method without creating an instance of the class containing it.
*   **Hinglish:** JVM ko class ka object na banana pade run karne se pehle, isliye ise static banate hain.

#### Q7: What is the signature of the main method?
*   **Answer:** `public static void main(String[] args)`.
*   **Hinglish:** `public` (sabko accessible), `static` (no object needed), `void` (no return value), `main` (entry point), `String[] args` (command line arguments).

#### Q8: Can we change the order of modifiers in `public static void main`?
*   **Answer:** Yes, `static public void main` is completely valid.
*   **Hinglish:** Modifiers ka order change kar sakte hain, par `void` humesha function name ke theek pehle aana chahiye.

#### Q9: What happens if you do not write `String[] args` in the main method?
*   **Answer:** The program compiles, but the JVM will not recognize it as the application entry point and throws a runtime error.
*   **Hinglish:** Compile ho jayega, par runtime pe execute nahi hoga kyunki JVM ko correct signature nahi milega.

#### Q10: What are package declarations in Java?
*   **Answer:** They group related classes. It is the first statement in a Java file.
*   **Hinglish:** Classes ko organize karne ke liye package use hota hai (jaise folder structure).

#### Q11: What is default value of local variables in Java?
*   **Answer:** Local variables have no default values. They must be initialized before use, otherwise, it causes a compilation error.
*   **Hinglish:** Class members ke paas default values hoti hain, par functions ke andar ke variables (local variables) ko initialize karna compulsory hai.

#### Q12: Explain widening and narrowing typecasting.
*   **Answer:** Widening (implicit) converts smaller type to larger type. Narrowing (explicit) converts larger type to smaller type.
*   **Hinglish:** Chote variable se bade variable mein data automatically transfer ho jata hai (widening). Bade se chote mein explicitly data cast karna padta hai (narrowing).
*   **Example:**
    ```java
    double d = 10.5;
    int x = (int) d; // Narrowing
    ```

#### Q13: Why does `System.out.println(10 + 20 + "Hello")` print `30Hello` but `System.out.println("Hello" + 10 + 20)` prints `Hello1020`?
*   **Answer:** Evaluation goes left-to-right. In the first case, integers are added first. In the second, the string concatenates integers sequentially.
*   **Hinglish:** Left-to-right calculation hoti hai. Agar string pehle aa jaye, toh baaki saari values string concat ban jaati hain.

#### Q14: What is the difference between float and double?
*   **Answer:** `float` is 32-bit single-precision. `double` is 64-bit double-precision (default for decimal values in Java).

#### Q15: What is the default type of a decimal literal in Java?
*   **Answer:** `double`. You must suffix `float` values with `f` (e.g. `float f = 5.5f;`).

#### Q16: What is garbage collection in Java?
*   **Answer:** It is an automatic background process that reclaims memory by destroying objects that are no longer reachable.
*   **Hinglish:** System automatically un objects ki memory free kar deta hai jinka reference ab kisi variable ke paas nahi hai.

#### Q17: Can we force garbage collection in Java?
*   **Answer:** No. We can suggest it using `System.gc()`, but JVM does not guarantee when it will run.
*   **Hinglish:** Hum `System.gc()` se request kar sakte hain, par call kab hoga yeh JVM ke upar hai.

#### Q18: What is the difference between static and instance variables?
*   **Answer:** Static variables are shared among all class objects. Instance variables are unique to each object instance.
*   **Hinglish:** Static class level pe hota hai (single copy), instance variable object level pe hota hai (nayi copy for each object).

#### Q19: Can a static method access non-static variables?
*   **Answer:** No. Static methods belong to the class, while non-static variables belong to specific object instances.
*   **Hinglish:** Static methods bina object ke chalte hain, isliye woh instance variable ko bina object reference ke access nahi kar sakte.

#### Q20: What is the `final` keyword in Java?
*   **Answer:** It makes variables constant, prevents method overriding, and stops inheritance for classes.
*   **Hinglish:** Value reassign nahi hone deta (constant), method override nahi hone deta, aur class inherit hone se rokta hai.

#### Q21: What is the difference between `const` and `final`?
*   **Answer:** Java does not use `const` (it is a reserved keyword but unused). `final` is used instead.

#### Q22: What is the default access modifier in Java?
*   **Answer:** `package-private` (default). Accessible only within the same package.

#### Q23: Explain public, private, and protected modifiers.
*   **Answer:**
    *   `public`: Accessible everywhere.
    *   `private`: Accessible only within the same class.
    *   `protected`: Accessible within the same package and by subclasses.

#### Q24: What is the wrapper class of `char`?
*   **Answer:** `Character` (not Char).
*   **Hinglish:** Char primitive type ka object representation class `Character` hai.

#### Q25: Why is Java compiled and interpreted?
*   **Answer:** Source code is compiled to bytecode by `javac`, which is then interpreted/JIT-compiled by the JVM.

---

## 📂 Section 2: Arrays, Strings, Methods & Memory (Q26 - Q50)

#### Q26: Does Java pass arguments by value or by reference?
*   **Answer:** Strictly by value. For objects, the copy of reference address is passed by value.
*   **Hinglish:** Primitives ki value copy hoti hai, aur objects ke reference address ki value copy hoti hai.
*   **Point:** Reference parameters cannot be reassigned to affect the caller.

#### Q27: How are arrays represented in memory?
*   **Answer:** The array reference variable is on the stack, while the actual elements are allocated on the heap.
*   **Hinglish:** Reference stack memory mein hota hai aur elements ka main container heap memory mein save hota hai.

#### Q28: What is the difference between `arr.length` and `str.length()`?
*   **Answer:** `arr.length` is a public property of arrays. `str.length()` is a public method of the String class.
*   **Hinglish:** Array ka size property se nikalta hai, String ka size method call se.
*   **Trap:** Writing `arr.length()` will give a compile error.

#### Q29: What is the default value of an uninitialized array element?
*   **Answer:** Numeric types: `0` or `0.0`. Booleans: `false`. Object references: `null`.

#### Q30: What is String immutability?
*   **Answer:** String objects cannot be modified after creation. Any change creates a new String object.
*   **Hinglish:** Memory mein string data safe rehta hai, use update karne pe nayi memory space locate hoti hai.

#### Q31: What is the String Constant Pool (SCP)?
*   **Answer:** A special memory region in heap where Java stores literal string values to optimize memory.
*   **Hinglish:** Duplicate strings se bachne ke liye Java pool mein literals store karta hai aur use repeat karta hai.

#### Q32: What is the difference between `==` and `.equals()` for Strings?
*   **Answer:** `==` compares reference addresses. `.equals()` compares the actual text content.
*   **Hinglish:** Address compare karne ke liye `==` use hoga, and characters compare karne ke liye `.equals()`.
*   **Trap:** Always use `.equals()` for logic.

#### Q33: How does `new String("hello")` work?
*   **Answer:** It creates two objects: one in the heap and one in the String Constant Pool (if not already present).
*   **Hinglish:** Dynamic `new` keyword heap mein alag object banata hai, pool ke bahar.

#### Q34: What is the difference between `String` and `StringBuilder`?
*   **Answer:** `String` is immutable and slow for modifications. `StringBuilder` is mutable and fast for additions.
*   **Hinglish:** String modify hone pe naya object banati hai (slow). StringBuilder in-place modify hota hai (fast).

#### Q35: Why does `StringBuilder` not have an `equals()` method?
*   **Answer:** It does not override Object's `equals()`. It inherits reference check behavior.
*   **Hinglish:** Comparator support check nahi karta. `.toString()` karke compare karna padta hai.

#### Q36: How do you reverse a String in Java?
*   **Answer:** Convert to `StringBuilder`, call `.reverse()`, and convert back using `.toString()`.
*   **Example:**
    ```java
    String rev = new StringBuilder(s).reverse().toString();
    ```

#### Q37: What is the `charAt(i)` method?
*   **Answer:** Returns the character at index `i` of a string.
*   **Trap:** Do not write `s[i]`. It is invalid in Java.

#### Q38: What does `String.substring(start, end)` return?
*   **Answer:** Returns a substring starting at `start` and ending at `end - 1` (exclusive).

#### Q39: What is the purpose of `String.trim()`?
*   **Answer:** Removes leading and trailing whitespaces from the string.

#### Q40: What is `String.split()`?
*   **Answer:** Splits a string into an array of strings based on a regex delimiter.
*   **Example:**
    ```java
    String[] parts = "A,B,C".split(","); // ["A", "B", "C"]
    ```

#### Q41: Explain memory leak in Java.
*   **Answer:** Occurs when unused objects are still referenced, preventing the Garbage Collector from freeing their memory.

#### Q42: What is Stack Overflow Error?
*   **Answer:** Occurs when stack memory is exhausted, commonly due to infinite recursion.

#### Q43: How do you copy an array in Java?
*   **Answer:** Use `Arrays.copyOf(arr, length)` or `.clone()`.
*   **Hinglish:** Re-assigning variable se sirf reference copy hota hai, copy creation ke liye utility method use karein.

#### Q44: What is an anonymous array?
*   **Answer:** An array created without a reference variable name.
*   **Example:** `new int[]{1, 2, 3}`.

#### Q45: Can we change the size of an array after declaration?
*   **Answer:** No. Arrays in Java are of fixed size once allocated.

#### Q46: What is the difference between null and empty string?
*   **Answer:** `null` means the reference variable does not point to any object. `""` is a valid string object of length 0.

#### Q47: What exception is thrown when array index is out of range?
*   **Answer:** `ArrayIndexOutOfBoundsException`.

#### Q48: What is `String.valueOf()`?
*   **Answer:** Converts primitives (like int, double) to their string representation.

#### Q49: Does Java support negative index access in arrays like Python?
*   **Answer:** No. Accessing negative index throws exception.

#### Q50: How do you search a character in a String?
*   **Answer:** Use `s.indexOf(ch)` or `s.contains(str)`.

---

## 📂 Section 3: Collections & OOP Basics (Q51 - Q75)

#### Q51: What is the Java Collection Framework?
*   **Answer:** A unified architecture providing data structures (like List, Set, Queue, Map) and algorithms (like sorting).

#### Q52: What is the difference between ArrayList and LinkedList?
*   **Answer:** `ArrayList` uses dynamic arrays (fast lookup $O(1)$, slow shift $O(N)$). `LinkedList` uses doubly-linked nodes (slow lookup $O(N)$, fast insert $O(1)$).

#### Q53: What is the difference between List and Set?
*   **Answer:** `List` allows duplicate elements and maintains insertion order. `Set` stores unique elements and does not guarantee order.

#### Q54: What is the difference between HashMap and HashSet?
*   **Answer:** `HashMap` stores key-value pairs. `HashSet` stores unique values (internally uses a HashMap with dummy values).

#### Q55: How does HashMap handle duplicate keys?
*   **Answer:** It replaces the old value with the new value for that key.

#### Q56: What is the average time complexity of HashMap lookup?
*   **Answer:** $O(1)$ on average.

#### Q57: How does HashMap handle collisions?
*   **Answer:** It uses chaining (linked lists) and converts chains to self-balancing BSTs (Red-Black Trees) if chain length exceeds 8.

#### Q58: What is `map.getOrDefault()`?
*   **Answer:** Returns key value if present, else returns a specified default value. Excellent for frequency maps.

#### Q59: Why can we not use primitives in collections?
*   **Answer:** Collections require object references. Primitives do not inherit from the Object class.

#### Q60: What is Autoboxing and Unboxing?
*   **Answer:**
    *   *Autoboxing:* Primitive $\rightarrow$ Wrapper Object (`int` to `Integer`).
    *   *Unboxing:* Wrapper Object $\rightarrow$ Primitive (`Integer` to `int`).

#### Q61: What is the difference between TreeMap and HashMap?
*   **Answer:** `HashMap` is unordered and runs in $O(1)$ average time. `TreeMap` is sorted and runs in $O(\log N)$ time.

#### Q62: What is the difference between HashSet and TreeSet?
*   **Answer:** `HashSet` is unordered, runs in $O(1)$ time. `TreeSet` keeps elements sorted, runs in $O(\log N)$ time.

#### Q63: How do you sort an ArrayList?
*   **Answer:** Use `Collections.sort(list)`.

#### Q64: What is the Comparator interface?
*   **Answer:** An interface used to define custom sorting orders.
*   **Example:**
    ```java
    list.sort((a, b) -> a - b);
    ```

#### Q65: What is the Comparable interface?
*   **Answer:** Defines natural sorting order for classes by implementing `compareTo()`.

#### Q66: What is the difference between Comparator and Comparable?
*   **Answer:** `Comparable` modifies the actual class to sort itself. `Comparator` is an external strategy passed for custom sort rules.

#### Q67: What is dynamic resizing of ArrayList?
*   **Answer:** When the array capacity is full, ArrayList creates a new larger array (typically 1.5x capacity) and copies old elements.

#### Q68: What is the difference between `Iterator` and enhanced for loop?
*   **Answer:** `Iterator` allows safe element removal during iteration. Enhanced for-loops throw modification errors if you attempt removal.

#### Q69: What is the capacity of an empty ArrayList by default?
*   **Answer:** 10 elements (after the first addition).

#### Q70: What is OOP?
*   **Answer:** Object-Oriented Programming based on classes, objects, inheritance, polymorphism, encapsulation, and abstraction.

#### Q71: What is the difference between method overloading and overriding?
*   **Answer:** Overloading occurs at compile-time (same method name, different parameters). Overriding occurs at runtime (subclass replaces parent method implementation).

#### Q72: Does Java support multiple inheritance?
*   **Answer:** Classes cannot inherit from multiple classes to avoid ambiguity (the diamond problem). However, interfaces allow multiple inheritance.

#### Q73: What is the difference between Abstract Class and Interface?
*   **Answer:** Abstract classes can have instance variables and constructors. Interfaces (before Java 8) could only have abstract methods and constants.

#### Q74: What is the `super` keyword?
*   **Answer:** Used to refer to immediate parent class variables, methods, or constructors.

#### Q75: What is encapsulation?
*   **Answer:** Wrapping variables and code logic inside a class, keeping variables private and exposing them through getter/setter methods.

---

## 📂 Section 4: Tricky Placement & Algorithmic Questions (Q76 - Q100)

#### Q76: What is the NullPointerException trap in unboxing?
*   **Answer:** Trying to unbox a `null` wrapper variable to primitive type throws `NullPointerException`.
*   **Example:**
    ```java
    Integer val = null;
    int num = val; // Throws NPE at runtime!
    ```

#### Q77: Why does `System.out.println(0.1 + 0.2)` output `0.30000000000000004`?
*   **Answer:** Floating-point representations are binary fractions, leading to small precision losses in arithmetic calculations.

#### Q78: How can you write a labeled break to escape nested loops?
*   **Answer:** Prefix loops with labels and call `break labelName;`.
*   **Example:**
    ```java
    outer: for(...) {
        for(...) {
            break outer;
        }
    }
    ```

#### Q79: Can we use `System.out.print` to format float limits?
*   **Answer:** Use `System.out.printf("%.2f", value)` similar to C++ `printf`.

#### Q80: Why must the array/search space be sorted for Binary Search?
*   **Answer:** Binary Search assumes that elements are ordered. If $arr[mid] < target$, it assumes the target can only be to the right of $mid$, which fails if unsorted.
*   **Hinglish:** Sorted hoga tabhi toh decide kar payenge ki right jana hai ya left. Unsorted mein is boundary check ka koi matlab nahi rehta.

#### Q81: What is string concatenation inside a loop time complexity?
*   **Answer:** $O(N^2)$ due to allocation of new string copies at each iteration.

#### Q82: How do you sort a primitive array in descending order?
*   **Answer:** You cannot pass `Collections.reverseOrder()` to `int[]`. You must use `Integer[]` or sort and reverse manually.
*   **Trap:** `Arrays.sort(intArray, Collections.reverseOrder())` fails compilation.

#### Q83: What is the ternary operator type verification rule?
*   **Answer:** Both result values in ternary checks must evaluate to compatible types.

#### Q84: How do you convert a List of Strings to a String Array?
*   **Answer:** Use `list.toArray(new String[0])`.

#### Q85: What is the difference between `std::unordered_map` and `HashMap`?
*   **Answer:** C++ `unordered_map` handles missing keys by auto-inserting them. Java `HashMap` returns `null` for missing keys.

#### Q86: What is the C++ `std::vector` equivalent of `clear()` in ArrayList?
*   **Answer:** Both are named `.clear()`.

#### Q87: What is the range of values cached by Integer class?
*   **Answer:** $-128$ to $127$. Comparing two `Integer` objects within this range using `==` returns `true`. Outside this range, it checks references and returns `false`.

#### Q88: How do you calculate `mid` safely in Java to prevent overflow?
*   **Answer:** Use `int mid = low + (high - low) / 2;` instead of `(low + high) / 2`.
*   **Hinglish:** `low + high` karne par agar variable key capacity boundary (2147483647) cross ho jaye toh negative result dega (overflow trap). `low + (high - low)/2` isse bachata hai.

#### Q89: What is the difference between Lower Bound and Upper Bound?
*   **Answer:** Lower Bound returns index of first element $\ge$ target. Upper Bound returns index of first element $>$ target.

#### Q90: What is the concept of Binary Search on Answer?
*   **Answer:** Binary searching on a monotonic search space of potential values (answers) and validating each step using a helper method.

#### Q91: Why is Binary Search $O(\log N)$?
*   **Answer:** Because it halves the search space at each iteration. Reducing $N$ to $1$ takes $\log_2(N)$ divisions.
*   **Hinglish:** Har check par search space aadhi ho jati hai, isliye time $\log N$ hota hai.

#### Q92: What is the difference between Iterative and Recursive Binary Search?
*   **Answer:** Iterative uses a while loop and runs in $O(1)$ space. Recursive calls itself and takes $O(\log N)$ auxiliary stack space.

#### Q93: What is recursion?
*   **Answer:** A programming technique where a method calls itself to solve smaller sub-problems.

#### Q94: What is a recursion base case, and what happens if it is missing?
*   **Answer:** The termination condition. If missing, the recursion calls itself infinitely, exhausting call stack memory and throwing `StackOverflowError`.

#### Q95: What happens internally in the JVM when a method calls itself recursively?
*   **Answer:** JVM pushes a new stack frame (containing arguments and local variables) onto the thread call stack. It pops frames when returning.

#### Q96: What is recursion stack space complexity?
*   **Answer:** The maximum depth of active stack frames on the call stack, typically equal to $O(H)$ where $H$ is recursion tree height.

#### Q97: What is the difference between Recursion and Iteration?
*   **Answer:** Iteration uses loops, runs in $O(1)$ space, and has low overhead. Recursion is cleaner for tree/subset structures but has $O(N)$ stack memory overhead.

#### Q98: Why does recursion cause a `StackOverflowError` in Java?
*   **Answer:** Because call stack size is limited. Deep recursion allocations consume all stack memory.

#### Q99: What is the Include/Exclude (Pick/Not Pick) recursion pattern?
*   **Answer:** A backtracking technique that decides to either include an element or exclude it, branching the recursion tree to generate subsets/subsequences.

#### Q100: How do memory allocations work for variables in Java?
*   **Answer:** Stack memory stores primitive variables and reference variables. Heap memory stores all class objects, collection objects, and array elements.
