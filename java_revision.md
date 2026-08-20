# Java Quick Revision Sheet

This guide serves as a cheat sheet for C++ developers to revise Java concepts quickly before a placement coding test.

---

## ⚡ C++ STL → Java Collections Mapping

| C++ STL | Java Collection Class | Package to Import |
|---|---|---|
| `std::vector<T>` | `ArrayList<T>` | `import java.util.ArrayList;` |
| `std::unordered_map<K, V>` | `HashMap<K, V>` | `import java.util.HashMap;` |
| `std::unordered_set<T>` | `HashSet<T>` | `import java.util.HashSet;` |
| `std::map<K, V>` | `TreeMap<K, V>` | `import java.util.TreeMap;` |
| `std::set<T>` | `TreeSet<T>` | `import java.util.TreeSet;` |
| `std::pair<T1, T2>` | Custom class OR `int[]` for coordinates | No direct equivalent; use simple array |
| `std::priority_queue<T>` | `PriorityQueue<T>` | `import java.util.PriorityQueue;` |
| `std::string` | `String` (Immutable) or `StringBuilder` (Mutable) | Default (`java.lang.*`) |

---

## 💻 Code Snippet Translation Cheat Sheet

### 1. Variables & Types
*   **C++:** `long long x = 10000LL;`
*   **Java:** `long x = 10000L;`
*   **C++:** `bool flag = true;`
*   **Java:** `boolean flag = true;`

### 2. Output
*   **C++:** `cout << "Val: " << x << endl;`
*   **Java:** `System.out.println("Val: " + x);`

### 3. Strings
*   **C++:** `char c = s[i];`
*   **Java:** `char c = s.charAt(i);`
*   **C++:** `if (s == t)`
*   **Java:** `if (s.equals(t))`

### 4. Basic Array
*   **C++:** `int arr[10];`
*   **Java:** `int[] arr = new int[10];`
*   **C++:** `int size = sizeof(arr)/sizeof(arr[0]);`
*   **Java:** `int size = arr.length;`

---

## 🪤 Common Java Coding Traps

1.  **Scanner Newline Trap:**
    After using `sc.nextInt()`, the newline character is left in the buffer. Running `sc.nextLine()` immediately after will read an empty string.
    *Fix:* Insert an extra `sc.nextLine();` to clear the buffer.
2.  **String Immuta-Trap:**
    Appending chars to a `String` inside a loop (`s += ch`) takes $O(N^2)$ time.
    *Fix:* Always use `StringBuilder sb` and `sb.append(ch)`.
3.  **Map key check Trap:**
    Accessing a non-existent key with `map.get(key)` returns `null`. Attempting to use it directly as a primitive `int` throws a `NullPointerException`.
    *Fix:* Use `map.getOrDefault(key, 0)`.
4.  **Reference Copying:**
    Writing `int[] b = a;` makes `b` point to the same memory as `a`. Changing `b[0]` modifies `a[0]`.
    *Fix:* Use `Arrays.copyOf(a, a.length)`.
5.  **Wrapper Equality:**
    Comparing wrapper objects using `==` (e.g. `Integer a == Integer b`) checks memory addresses, not numerical values (outside range -128 to 127).
    *Fix:* Use `a.equals(b)` or explicit casting `(int)a == (int)b`.

---

## ⏱️ Final 10-Minute Java Revision Checklist

- [ ] **String operations:** `.length()`, `.charAt()`, `.substring(start, end)` (exclusive), `.equals()`, `.toCharArray()`.
- [ ] **StringBuilder operations:** `append()`, `deleteCharAt()`, `setCharAt()`, `reverse()`, `toString()`.
- [ ] **ArrayList operations:** `add()`, `get()`, `set()`, `remove()`, `size()`, `Collections.sort()`.
- [ ] **HashMap operations:** `put()`, `get()`, `containsKey()`, `getOrDefault()`, `keySet()`.
- [ ] **HashSet operations:** `add()`, `contains()`, `remove()`.
- [ ] **Math functions:** `Math.max()`, `Math.min()`, `Math.abs()`, `Math.pow()`.
- [ ] **Limits:** `Integer.MAX_VALUE`, `Integer.MIN_VALUE`, `Long.MAX_VALUE`.
- [ ] **Compilation:** `javac Main.java` and execution `java Main`.
- [ ] **Strict Conditions:** Ensure loop and if checks are boolean expressions only. No `if (1)` is allowed.
