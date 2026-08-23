Bilkul papa 🔥 Ab ArrayList ko C++ ke vector ki tarah zero → advanced level tak ek complete toolkit ki tarah karte hain.

Tumhara objective sahi hai: pehle ArrayList ke saare important weapons/functions/syntax jaan lo, phir questions mein jab koi operation aaye to language ki wajah se rukna na pade.

C++ vector ≈ Java ArrayList

Java ka Vector alag legacy/synchronized class hai; DSA/LeetCode ke liye hum ArrayList ko primary dynamic-array structure maanenge.

# 🚀 JAVA ARRAYLIST — ZERO → ADVANCED COMPLETE TOOLKIT

## 0. Sabse pehle: Array vs ArrayList

### Normal Array

```java
int[] arr = new int[5];
```

Size fixed:

```text
5 → fixed
```

### ArrayList

```java
ArrayList<Integer> list = new ArrayList<>();
```

Size dynamically grow/shrink kar sakta hai.

- `add` → size badh sakta hai
- `remove` → size kam ho sakta hai

### C++ comparison

```cpp
vector<int> v;
```

Java:

```java
ArrayList<Integer> list = new ArrayList<>();
```

## 1. Import karna

Sabse pehle:

```java
import java.util.ArrayList;
```

Agar sorting/searching bhi karni hai:

```java
import java.util.Collections;
```

Ya simply:

```java
import java.util.*;
```

DSA practice mein `java.util.*` convenient hai.

## 2. Basic ArrayList banana

```java
ArrayList<Integer> list = new ArrayList<>();
```

Meaning:

- `ArrayList` → dynamic array
- `Integer`   → elements ka type
- `list`      → variable name

Example:

```java
import java.util.*;

public class ArrayListBasic {
    public static void main(String[] args) {

        ArrayList<Integer> list = new ArrayList<>();

        System.out.println(list);
    }
}
```

Output:

```text
[]
```

## 3. Important: Integer, not int

Ye:

```java
ArrayList<int> list;
```

❌ Invalid hai.

Ye:

```java
ArrayList<Integer> list;
```

✅ Correct.

Similarly:

- `int`     → `Integer`
- `long`    → `Long`
- `double`  → `Double`
- `char`    → `Character`
- `boolean` → `Boolean`

Inhe Wrapper Classes kehte hain.

## 4. Elements add karna — add() ⭐

Sabse basic weapon:

```java
list.add(10);
list.add(20);
list.add(30);
```

Now:

```text
[10, 20, 30]
```

Complete:

```java
import java.util.*;

public class AddExample {
    public static void main(String[] args) {

        ArrayList<Integer> list = new ArrayList<>();

        list.add(10);
        list.add(20);
        list.add(30);

        System.out.println(list);
    }
}
```

Output:

```text
[10, 20, 30]
```

## 5. Add at a particular index

```java
list.add(1, 100);
```

Suppose:

```text
[10, 20, 30]
```

After:

```java
list.add(1, 100);
```

becomes:

```text
[10, 100, 20, 30]
```

### Syntax

```java
list.add(index, value);
```

## 6. Size — size() ⭐⭐⭐

Array mein:

```java
arr.length
```

ArrayList mein:

```java
list.size()
```

Example:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);

System.out.println(list.size());
```

Output:

```text
3
```

⚠️ Difference:

```java
arr.length
```

vs

```java
list.size()
```

ArrayList mein `size()` method hai, isliye `()` lagta hai.

## 7. Element access — get() ⭐⭐⭐

Array:

```java
arr[2]
```

ArrayList:

```java
list.get(2)
```

Example:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);

System.out.println(list.get(1));
```

Output:

```text
20
```

## 8. Element change — set() ⭐⭐⭐

Array:

```java
arr[1] = 100;
```

ArrayList:

```java
list.set(1, 100);
```

Example:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);

list.set(1, 100);

System.out.println(list);
```

Output:

```text
[10, 100, 30]
```

### Remember

- `get()` → value nikalna
- `set()` → value replace karna

## 9. Remove by index — remove(index)

```java
list.remove(1);
```

Suppose:

```text
[10, 20, 30]
```

After:

```java
list.remove(1);
```

→

```text
[10, 30]
```

## 🔥 10. remove(Integer.valueOf(x))

Ye Java ArrayList ka bahut important trap hai.

Suppose:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);
```

Agar likho:

```java
list.remove(20);
```

Java ise index 20 samajhne ki koshish karega, value 20 nahi.

Value remove karni ho:

```java
list.remove(Integer.valueOf(20));
```

Now:

```text
[10, 30]
```

🔥 LeetCode mein ye distinction useful hai.

## 11. Check element — contains()

```java
list.contains(20);
```

Returns:

```text
true / false
```

Example:

```java
if (list.contains(20)) {
    System.out.println("Found");
}
```

## 12. Find index — indexOf()

```java
list.indexOf(20);
```

Example:

```text
[10, 20, 30]
```

```java
list.indexOf(20);
```

returns:

```text
1
```

Agar element nahi mila:

```text
-1
```

## 13. Last occurrence — lastIndexOf()

Suppose:

```text
[10, 20, 10, 30, 10]
```

```java
list.lastIndexOf(10);
```

returns:

```text
4
```

## 14. Empty check — isEmpty()

```java
list.isEmpty()
```

Returns:

```text
true
```

if list empty hai.

Example:

```java
if (list.isEmpty()) {
    System.out.println("Empty");
}
```

## 15. Clear entire list — clear()

```java
list.clear();
```

Before:

```text
[10, 20, 30]
```

After:

```text
[]
```

## 16. ArrayList traverse karna — normal for ⭐⭐⭐

```java
for (int i = 0; i < list.size(); i++) {
    System.out.println(list.get(i));
}
```

Ye DSA ke liye extremely important hai.

### Thinking

```text
i = 0 → list.get(0)
i = 1 → list.get(1)
i = 2 → list.get(2)
...
```

## 17. For-each loop ⭐⭐⭐

```java
for (int x : list) {
    System.out.println(x);
}
```

Example:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);

for (int x : list) {
    System.out.println(x);
}
```

Output:

```text
10
20
30
```

### Rule

Index chahiye:

```java
for (int i = 0; i < list.size(); i++)
```

Sirf values chahiye:

```java
for (int x : list)
```

## 18. ArrayList with String

```java
ArrayList<String> names = new ArrayList<>();

names.add("Aman");
names.add("Rahul");
names.add("Bhavishya");
```

Traversal:

```java
for (String name : names) {
    System.out.println(name);
}
```

## 19. ArrayList with Character

```java
ArrayList<Character> chars = new ArrayList<>();

chars.add('a');
chars.add('b');
chars.add('c');
```

## 20. ArrayList with Double

```java
ArrayList<Double> prices = new ArrayList<>();

prices.add(10.5);
prices.add(20.5);
```

## 21. Sorting — Collections.sort() ⭐⭐⭐

Ascending order:

```java
Collections.sort(list);
```

Example:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(5);
list.add(2);
list.add(8);
list.add(1);

Collections.sort(list);

System.out.println(list);
```

Output:

```text
[1, 2, 5, 8]
```

## 22. Descending sort

```java
Collections.sort(list, Collections.reverseOrder());
```

Example:

```text
[5, 2, 8, 1]
```

becomes:

```text
[8, 5, 2, 1]
```

## 23. Reverse ArrayList ⭐⭐

```java
Collections.reverse(list);
```

Example:

```text
[1, 2, 3, 4, 5]
```

becomes:

```text
[5, 4, 3, 2, 1]
```

## 24. Maximum element

```java
int max = Collections.max(list);
```

Example:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(50);
list.add(20);

System.out.println(Collections.max(list));
```

Output:

```text
50
```

## 25. Minimum element

```java
int min = Collections.min(list);
```

Output:

```text
10
```

## 26. Frequency — Collections.frequency()

Suppose:

```text
[10, 20, 10, 30, 10]
```

```java
Collections.frequency(list, 10);
```

returns:

```text
3
```

Useful for basic frequency problems.

## 27. Swap elements

```java
Collections.swap(list, i, j);
```

Example:

```java
Collections.swap(list, 0, 2);
```

If:

```text
[10, 20, 30]
```

becomes:

```text
[30, 20, 10]
```

## 28. Fill entire ArrayList

```java
Collections.fill(list, 0);
```

Suppose:

```text
[10, 20, 30]
```

becomes:

```text
[0, 0, 0]
```

## 29. Copy ArrayList

Basic independent copy:

```java
ArrayList<Integer> copy = new ArrayList<>(list);
```

Example:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);

ArrayList<Integer> copy = new ArrayList<>(list);
```

Now both contain:

```text
[10, 20]
```

## ⚠️ 30. Reference copy vs actual copy

Ye important hai.

```java
ArrayList<Integer> b = a;
```

Ye new ArrayList nahi banata.

`a` aur `b` same underlying object ko refer karenge.

Independent copy:

```java
ArrayList<Integer> b = new ArrayList<>(a);
```

DSA mein jab copy modify karni ho, second approach useful hai.

## 31. Capacity kya hoti hai?

ArrayList internally ek dynamic array use karta hai.

Conceptually:

- `size`     → currently kitne elements
- `capacity` → internally kitni space allocated

Example:

```java
ArrayList<Integer> list = new ArrayList<>();
```

Initially size:

```text
0
```

`add()` karte jao to internally capacity grow hoti hai.

Important: exact growth implementation detail par depend karti hai; isliye DSA mein fixed "2x" rule assume mat karna.

## 32. Initial capacity dena

```java
ArrayList<Integer> list = new ArrayList<>(100);
```

Isse initial internal capacity reserve karne ka hint milta hai.

Lekin:

```java
list.size()
```

phir bhi:

```text
0
```

hoga.

🔥 Capacity aur size same cheez nahi hain.

## 33. ArrayList → Array ⭐⭐⭐

Suppose:

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);
```

Primitive `int[]` mein convert karne ke liye simple approach:

```java
int[] arr = new int[list.size()];

for (int i = 0; i < list.size(); i++) {
    arr[i] = list.get(i);
}
```

Ye DSA mein bahut useful hai.

## 34. Array → ArrayList ⭐⭐⭐

Suppose:

```java
int[] arr = {10, 20, 30};
```

Primitive array ko directly:

```java
new ArrayList<>(Arrays.asList(arr))
```

❌ mat karo — `int[]` ke saath ye expected `ArrayList<Integer>` nahi deta.

Safe/simple DSA approach:

```java
ArrayList<Integer> list = new ArrayList<>();

for (int x : arr) {
    list.add(x);
}
```

## 35. String array → ArrayList

Ye easy hai:

```java
String[] arr = {"A", "B", "C"};

ArrayList<String> list =
        new ArrayList<>(Arrays.asList(arr));
```

Now:

```text
[A, B, C]
```

## 36. Arrays.asList() ka important limitation

```java
List<Integer> list = Arrays.asList(1, 2, 3);
```

Ye fixed-size backed list hoti hai.

Isliye:

```java
list.add(4);
```

❌ generally `UnsupportedOperationException`.

Mutable `ArrayList` chahiye:

```java
ArrayList<Integer> list =
        new ArrayList<>(Arrays.asList(1, 2, 3));
```

Now:

```java
list.add(4);
```

✅

## 37. subList() ⭐⭐⭐

List ka ek portion:

```java
List<Integer> sub = list.subList(1, 4);
```

Suppose:

```text
[10, 20, 30, 40, 50]
```

Then:

```java
list.subList(1, 4)
```

gives:

```text
[20, 30, 40]
```

⚠️ End index exclusive hota hai.

Same concept:

`[start, end)`

## 38. Remove a range

Agar:

```text
[10, 20, 30, 40, 50]
```

aur:

```java
list.subList(1, 4).clear();
```

to:

```text
[10, 50]
```

Useful technique hai.

## 39. addAll() ⭐⭐⭐

Ek list ko doosri mein add karna:

```java
list1.addAll(list2);
```

Example:

```text
list1 = [1, 2]
list2 = [3, 4]
```

After:

```java
list1.addAll(list2);
```

```text
[1, 2, 3, 4]
```

## 40. removeAll()

Common elements remove karne ke liye:

```java
list1.removeAll(list2);
```

Conceptually `list1` se woh elements remove karega jo `list2` mein present hain.

## 41. retainAll()

Sirf common elements retain karna:

```java
list1.retainAll(list2);
```

Ye intersection-type operations mein useful ho sakta hai.

## 42. containsAll()

Check:

```java
list1.containsAll(list2);
```

Agar `list1` mein `list2` ke saare elements hain:

```text
true
```

otherwise:

```text
false
```

## 43. equals()

Do lists compare:

```java
list1.equals(list2)
```

Example:

```text
[1, 2, 3]
[1, 2, 3]
```

→ `true`

Order matter karta hai.

```text
[1, 2, 3]
[3, 2, 1]
```

→ `false`

## 44. Empty ArrayList

```java
ArrayList<Integer> list = new ArrayList<>();
```

or:

```java
ArrayList<Integer> list = new ArrayList<>(0);
```

Normally first one use karo.

## 45. 2D ArrayList 🔥🔥🔥

Ye LeetCode ke liye bahut important hai.

C++:

```cpp
vector<vector<int>> v;
```

Java:

```java
ArrayList<ArrayList<Integer>> list = new ArrayList<>();
```

Example:

```java
ArrayList<ArrayList<Integer>> matrix = new ArrayList<>();

ArrayList<Integer> row1 = new ArrayList<>();
row1.add(1);
row1.add(2);
row1.add(3);

matrix.add(row1);
```

Result:

```text
[[1, 2, 3]]
```

## 46. 2D ArrayList create karna

Suppose 3 rows:

```java
ArrayList<ArrayList<Integer>> matrix = new ArrayList<>();

for (int i = 0; i < 3; i++) {
    matrix.add(new ArrayList<>());
}
```

Now:

```text
[
 [],
 [],
 []
]
```

Elements add:

```java
matrix.get(0).add(10);
matrix.get(1).add(20);
matrix.get(2).add(30);
```

## 47. 2D ArrayList access

`matrix.get(i).get(j)`

C++:

```cpp
v[i][j]
```

Java:

```java
matrix.get(i).get(j)
```

🔥 Ye difference yaad rakho.

## 48. 2D ArrayList traversal

```java
for (int i = 0; i < matrix.size(); i++) {

    for (int j = 0; j < matrix.get(i).size(); j++) {

        System.out.print(matrix.get(i).get(j) + " ");
    }

    System.out.println();
}
```

## 49. ArrayList of Strings

```java
ArrayList<String> words = new ArrayList<>();
```

Traversal:

```java
for (String word : words) {
    System.out.println(word);
}
```

String-related problems mein useful.

## 50. ArrayList of custom objects

OOP mein:

```java
ArrayList<Student> students = new ArrayList<>();
```

Ye advanced Java mein aayega.

LeetCode mein bhi custom classes/objects wale problems mein kaam aa sakta hai.

## 51. ArrayList + Stack type operations

ArrayList ke end ko stack ki tarah use kar sakte ho:

```java
list.add(x);              // push
list.get(list.size()-1);  // top
list.remove(list.size()-1); // pop
```

But dedicated stack/deque structures ke liye hum later `ArrayDeque` padhenge.

## 52. ArrayList + Binary Search

Sorted list:

```java
Collections.sort(list);
```

Then:

```java
int index = Collections.binarySearch(list, target);
```

Example:

```java
ArrayList<Integer> list =
        new ArrayList<>(Arrays.asList(1, 3, 5, 7, 9));

int index = Collections.binarySearch(list, 7);

System.out.println(index);
```

Output:

```text
3
```

⚠️ Sorted list required for meaningful binary-search behavior.

## 53. Custom sorting — Comparator 🔥🔥

Ye advanced aur very useful hai.

Ascending:

```java
list.sort(Integer::compareTo);
```

Descending:

```java
list.sort(Collections.reverseOrder());
```

Custom objects mein:

```java
students.sort((a, b) -> a.age - b.age);
```

Ya safer comparator:

```java
students.sort((a, b) -> Integer.compare(a.age, b.age));
```

Isko hum Comparator ke dedicated topic mein deeply karenge.

## 54. ArrayList ka toString()

Simply:

```java
System.out.println(list);
```

prints:

```text
[10, 20, 30]
```

Isliye debugging easy hai.

## 55. ArrayList as method parameter

LeetCode-style functions mein:

```java
static void printList(ArrayList<Integer> list) {

    for (int x : list) {
        System.out.println(x);
    }
}
```

Call:

```java
printList(list);
```

## 56. ArrayList as return type

```java
static ArrayList<Integer> createList() {

    ArrayList<Integer> list = new ArrayList<>();

    list.add(10);
    list.add(20);

    return list;
}
```

This is very important for problems where answer itself is a list.

## 57. LeetCode mein ArrayList ka important use ⭐⭐⭐

Example problem asks:

Return all values satisfying some condition.

You can:

```java
ArrayList<Integer> ans = new ArrayList<>();

for (int x : nums) {

    if (x % 2 == 0) {
        ans.add(x);
    }
}
```

Then depending on required return type:

```java
return ans;
```

or convert to array.

## 58. ArrayList<Integer> aur int[] ka difference

Ye bahut important hai because LeetCode problem statement decide karega tumhe kya return karna hai.

Problem gives:
`int[] nums`

Tum directly:

`nums[i]`

use karoge.

Agar answer:
`List<Integer>`

chahiye:

```java
List<Integer> ans = new ArrayList<>();
```

Agar answer:
`int[]`

chahiye:

```java
int[] ans = new int[n];
```

Question ka required return type dekhna hamesha important hai.

## 59. ArrayList ka time complexity toolkit

Average/amortized understanding:

| Operation | Typical Complexity |
| :--- | :--- |
| `get(i)` | `O(1)` |
| `set(i,x)` | `O(1)` |
| `add(x)` at end | `O(1)` amortized |
| `add(i,x)` | `O(n)` |
| `remove(i)` | `O(n)` |
| `contains(x)` | `O(n)` |
| `indexOf(x)` | `O(n)` |
| `sort()` | `O(n log n)` |
| `Collections.reverse()` | `O(n)` |

### Why add(i,x) O(n)?

Because elements shift karne pad sakte hain.

Example:

```text
[10,20,30,40]
```

Insert 15 at index 1:

```text
[10,15,20,30,40]
```

`20,30,40` shift hue.

## 60. ArrayList internally kaise sochna hai?

Conceptually:

```text
ArrayList
   ↓
Dynamic backing array
   ↓
Elements contiguous-style storage
   ↓
Capacity full?
   ↓
Larger storage allocate
   ↓
Old elements copy
```

Isi wajah se end par `add()` amortized `O(1)` hota hai, lekin resizing ke particular moment par copying cost aa sakti hai.

## 🔥 61. ArrayList ke "MUST KNOW" weapons

Agar LeetCode ke liye minimum complete toolkit banana hai, ye absolutely yaad hone chahiye:

```java
ArrayList<Integer> list = new ArrayList<>();
```

- **Add**:
  ```java
  list.add(x);
  list.add(index, x);
  ```
- **Access**:
  ```java
  list.get(i);
  ```
- **Update**:
  ```java
  list.set(i, x);
  ```
- **Remove**:
  ```java
  list.remove(i);
  list.remove(Integer.valueOf(x));
  ```
- **Size**:
  ```java
  list.size();
  ```
- **Search**:
  ```java
  list.contains(x);
  list.indexOf(x);
  list.lastIndexOf(x);
  ```
- **Empty**:
  ```java
  list.isEmpty();
  ```
- **Clear**:
  ```java
  list.clear();
  ```
- **Sorting**:
  ```java
  Collections.sort(list);
  ```
- **Reverse**:
  ```java
  Collections.reverse(list);
  ```
- **Max/Min**:
  ```java
  Collections.max(list);
  ```
  ```java
  Collections.min(list);
  ```
- **Frequency**:
  ```java
  Collections.frequency(list, x);
  ```
- **Swap**:
  ```java
  Collections.swap(list, i, j);
  ```
- **Binary Search**:
  ```java
  Collections.binarySearch(list, x);
  ```
- **Merge/add another list**:
  ```java
  list.addAll(other);
  ```
- **Sublist**:
  ```java
  list.subList(l, r);
  ```
- **Copy**:
  ```java
  new ArrayList<>(list);
  ```

## 🧠 62. C++ Vector → Java ArrayList Cheat Sheet

Ye tumhare liye golden table hai:

| C++ Vector | Java ArrayList |
| :--- | :--- |
| `vector<int> v` | `ArrayList<Integer> list` |
| `v.push_back(x)` | `list.add(x)` |
| `v[i]` | `list.get(i)` |
| `v[i] = x` | `list.set(i,x)` |
| `v.size()` | `list.size()` |
| `v.pop_back()` | `list.remove(list.size()-1)` |
| `v.clear()` | `list.clear()` |
| `v.empty()` | `list.isEmpty()` |
| `find()` | `contains() / indexOf()` |
| `sort(v.begin(),v.end())` | `Collections.sort(list)` |
| `reverse()` | `Collections.reverse(list)` |
| `max_element()` | `Collections.max(list)` |
| `min_element()` | `Collections.min(list)` |
| `count()` | `Collections.frequency()` |
| `swap()` | `Collections.swap()` |
| `vector<vector<int>>` | `ArrayList<ArrayList<Integer>>` |

## ⚠️ 63. 5 Java ArrayList traps

- **Trap 1**:
  ```java
  list.length
  ```
  ❌
  ```java
  list.size()
  ```
  ✅

- **Trap 2**:
  ```java
  list[i]
  ```
  ❌
  ```java
  list.get(i)
  ```
  ✅

- **Trap 3**:
  ```java
  ArrayList<int>
  ```
  ❌
  ```java
  ArrayList<Integer>
  ```
  ✅

- **Trap 4**:
  ```java
  list.remove(10);
  ```
  This means index 10 for `ArrayList<Integer>`.
  
  Value 10 remove karna ho:
  
  ```java
  list.remove(Integer.valueOf(10));
  ```

- **Trap 5**:
  ```java
  Arrays.asList(intArray)
  ```
  primitive `int[]` ke saath expected `ArrayList<Integer>` nahi deta.
  
  Safe conversion:
  
  ```java
  ArrayList<Integer> list = new ArrayList<>();
  
  for (int x : arr) {
      list.add(x);
  }
  ```

## 🏆 ArrayList ka Complete Roadmap

Ab tumhare ArrayList chapter ko hum mentally is tarah divide kar sakte hain:

```text
ARRAYLIST
│
├── Basic
│   ├── Create
│   ├── Add
│   ├── Get
│   ├── Set
│   ├── Remove
│   └── Size
│
├── Search
│   ├── contains
│   ├── indexOf
│   └── lastIndexOf
│
├── Utility
│   ├── sort
│   ├── reverse
│   ├── max
│   ├── min
│   ├── frequency
│   └── swap
│
├── Bulk Operations
│   ├── addAll
│   ├── removeAll
│   ├── retainAll
│   ├── containsAll
│   └── clear
│
├── Conversion
│   ├── Array → ArrayList
│   └── ArrayList → Array
│
├── Advanced
│   ├── subList
│   ├── Comparator
│   ├── binarySearch
│   ├── custom objects
│   └── 2D ArrayList
│
└── DSA
    ├── Two Pointer
    ├── Sliding Window
    ├── Prefix Sum
    ├── Hashing
    ├── Matrix
    └── Backtracking / Recursion
```

## 🔥 Ab tumhare liye important sequence

Theory ke liye ArrayList ka complete toolkit upar cover ho gaya. Ab isko ratne ki zarurat nahi hai.

Next practical phase mein hum alag files mein ArrayList ke basic programs karenge, exactly jaise tumne Java basics mein kiya:

- `01_ArrayListCreate.java`
- `02_ArrayListAdd.java`
- `03_ArrayListGet.java`
- `04_ArrayListSet.java`
- `05_ArrayListRemove.java`
- ...

Phir ArrayList + actual LeetCode questions mein use karenge. Isse vector → ArrayList conversion automatically natural ho jayega. 🔥
