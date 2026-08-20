# Chapter 11 — HashMap & HashSet ⭐⭐⭐

### 1. What is it?
*   `HashMap` is a hash-table-based implementation of the `Map` interface. It stores data in key-value pairs (equivalent to `std::unordered_map` in C++).
*   `HashSet` is a hash-table-based implementation of the `Set` interface. It stores unique values (equivalent to `std::unordered_set` in C++).

### 2. Why do I need it for placements?
Hashing is the most important concept in coding assessments. Checking duplicates, frequency counts, and building maps for indices (like in the Two Sum problem) are core operations that require hashing.

### 3. C++ → Java Comparison
*   **HashMap Comparison:**
    *   C++: `unordered_map<int, int> mp;`
    *   Java: `HashMap<Integer, Integer> map = new HashMap<>();`
*   **HashSet Comparison:**
    *   C++: `unordered_set<int> st;`
    *   Java: `HashSet<Integer> set = new HashSet<>();`
*   **Common Method Mapping (HashMap):**

| C++ `unordered_map` | Java `HashMap` |
|---|---|
| `mp[key] = val` | `map.put(key, val)` |
| `mp[key]` or `mp.at(key)` | `map.get(key)` |
| `mp.count(key)` or `find()` | `map.containsKey(key)` |
| `mp.erase(key)` | `map.remove(key)` |
| `mp.size()` | `map.size()` |

*   **Common Method Mapping (HashSet):**

| C++ `unordered_set` | Java `HashSet` |
|---|---|
| `st.insert(x)` | `set.add(x)` |
| `st.count(x)` | `set.contains(x)` |
| `st.erase(x)` | `set.remove(x)` |

### 4. C++ Syntax/Example
```cpp
#include <iostream>
#include <unordered_map>
#include <unordered_set>
using namespace std;

int main() {
    unordered_map<string, int> mp;
    mp["apple"] = 5;
    
    if (mp.count("apple")) {
        cout << "Apple count: " << mp["apple"] << endl;
    }
    
    unordered_set<int> s;
    s.insert(10);
    if (s.count(10)) cout << "Set has 10" << endl;
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
import java.util.HashMap;
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {
        HashMap<String, Integer> map = new HashMap<>();
        map.put("apple", 5);
        
        if (map.containsKey("apple")) {
            System.out.println("Apple count: " + map.get("apple"));
        }
        
        HashSet<Integer> set = new HashSet<>();
        set.add(10);
        if (set.contains(10)) {
            System.out.println("Set has 10");
        }
    }
}
```

### 6. Important Java Differences
*   **`getOrDefault()` Utility:** Java maps have a highly convenient method `map.getOrDefault(key, defaultValue)`. If the key exists, it returns its value; otherwise, it returns the specified default value. This is perfect for frequency counting.
*   **Iteration Pattern:**
    *   To iterate over keys: `for (int key : map.keySet())`
    *   To iterate over key-value pairs:
        ```java
        for (HashMap.Entry<String, Integer> entry : map.entrySet()) {
            System.out.println(entry.getKey() + " -> " + entry.getValue());
        }
        ```
*   **Time Complexity:** Both `HashMap` and `HashSet` provide \(O(1)\) average time complexity for lookups, insertions, and deletions.

### 7. Simple Hinglish Explanation
C++ mein `unordered_map` aur `unordered_set` use hote the fast dynamic key-value storage aur unique collections ke liye. Java mein hum `HashMap` aur `HashSet` use karte hain.
Sabse best difference `map.getOrDefault(key, 0)` ka hai. C++ mein hum map value read karne ke liye direct `mp[key]` karte the toh value automatically `0` initialize ho jati thi. Java mein agar key nahi hai aur aapne `.get(key)` call kiya, toh woh `null` return karega (jisse `NullPointerException` aa sakta hai). Isliye, hum frequency check karne ke liye `map.put(key, map.getOrDefault(key, 0) + 1)` pattern use karte hain.

### 8. Small Practical Examples
Let's see frequency counting pattern:
```java
import java.util.HashMap;

public class Main {
    public static void main(String[] args) {
        int[] arr = {1, 2, 2, 3, 1, 2, 4};
        HashMap<Integer, Integer> freqMap = new HashMap<>();
        
        // Count frequencies
        for (int num : arr) {
            freqMap.put(num, freqMap.getOrDefault(num, 0) + 1);
        }
        
        // Print frequencies
        for (int key : freqMap.keySet()) {
            System.out.println(key + " occurs " + freqMap.get(key) + " times.");
        }
    }
}
```

### 9. Expected Output
```text
1 occurs 2 times.
2 occurs 3 times.
3 occurs 1 times.
4 occurs 1 times.
```

### 10. Common Mistakes
*   **Direct `.get(key)` on non-existent keys:** Doing `int val = map.get(key);` when the key is missing causes a runtime crash because Java returns `null`, and trying to unbox it to a primitive `int` throws a `NullPointerException`. Always use `getOrDefault(key, 0)` or check with `containsKey()`.
*   **Modifying Map during iteration:** Adding or removing keys while iterating directly over the map causes `ConcurrentModificationException`.

### 11. Interview Point
*   **What is the difference between HashMap and Hashtable/TreeMap?**
    *   `HashMap`: Single-threaded, allows one `null` key and multiple `null` values. \(O(1)\) time.
    *   `Hashtable`: Thread-safe (synchronized), does not allow null keys/values. Slow.
    *   `TreeMap`: Red-Black tree implementation. Keys are stored in sorted order. \(O(\log N)\) time. (Equivalent to `std::map` in C++).

### 12. Coding-Platform Usage
Here is the standard Two Sum problem template using `HashMap` in Java:
```java
public int[] twoSum(int[] nums, int target) {
    HashMap<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (map.containsKey(complement)) {
            return new int[] { map.get(complement), i };
        }
        map.put(nums[i], i);
    }
    return new int[] {}; // Target not found
}
```

### 13. Quick Revision
*   Map methods: `map.put(k, v)`, `map.get(k)`, `map.containsKey(k)`, `map.getOrDefault(k, defaultVal)`.
*   Set methods: `set.add(val)`, `set.contains(val)`, `set.remove(val)`.
*   Map traversal: Loop over `map.keySet()` or `map.entrySet()`.
*   Avoid direct `.get(key)` unboxing without validation.
