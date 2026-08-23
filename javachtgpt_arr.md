🚀 JAVA ARRAYS — COMPLETE FOUNDATION
1. Array kya hota hai?

Array ek data structure hai jo same data type ki multiple values ko ek hi variable mein store karta hai.

Without array:

int a = 10;
int b = 20;
int c = 30;
int d = 40;
int e = 50;

Array ke saath:

int[] arr = {10, 20, 30, 40, 50};

Visualize:

Index:    0   1   2   3   4
          ↓   ↓   ↓   ↓   ↓
arr:     10  20  30  40  50

⚠️ Java array ka index 0 se start hota hai.

2. Array declare kaise karte hain?

Do common ways:

int[] arr;

ya:

int arr[];

Dono valid hain.

But hum recommended style use karenge:

int[] arr;
3. Array create karna
int[] arr = new int[5];

Iska matlab:

5 integers store karne ki capacity ka array banao.

Initially values:

Index:  0   1   2   3   4
Value:  0   0   0   0   0

Primitive int array ke elements initially 0 hote hain.

4. Array mein value store karna
int[] arr = new int[5];

arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
arr[3] = 40;
arr[4] = 50;

Array:

Index:  0   1   2   3   4
Value: 10  20  30  40  50
5. Array se value access karna
System.out.println(arr[0]);

Output:

10
System.out.println(arr[3]);

Output:

40
Formula
First element → arr[0]
Second element → arr[1]
Last element → arr[n - 1]
6. Array initialize directly

Ye sabse commonly used syntax hai:

int[] arr = {10, 20, 30, 40, 50};

Ye:

int[] arr = new int[5];

arr[0] = 10;
arr[1] = 20;
arr[2] = 30;
arr[3] = 40;
arr[4] = 50;

ka shortcut hai.

LeetCode mein

Tum bahut frequently dekhoge:

int[] nums = {2, 7, 11, 15};
7. Array ki length 🔥

Java array ki length:

arr.length

Example:

int[] arr = {10, 20, 30, 40, 50};

System.out.println(arr.length);

Output:

5

⚠️ Important:

Java mein array ke liye:

arr.length

NOT

arr.length()

length property hai, method nahi.

8. Array traverse karna 🔥🔥

Ye DSA ka sabse important basic concept hai.

int[] arr = {10, 20, 30, 40, 50};

for (int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

Output:

10
20
30
40
50
Computer internally
i = 0 → arr[0]
i = 1 → arr[1]
i = 2 → arr[2]
i = 3 → arr[3]
i = 4 → arr[4]
i = 5 → stop

Condition:

i < arr.length

bahut important hai.

9. Reverse traversal
int[] arr = {10, 20, 30, 40, 50};

for (int i = arr.length - 1; i >= 0; i--) {
    System.out.println(arr[i]);
}

Output:

50
40
30
20
10

Ye reverse-array problems mein directly use hota hai.

10. Enhanced for loop / for-each 🔥

Java ka special array loop:

for (int x : arr) {
    System.out.println(x);
}

Example:

int[] arr = {10, 20, 30, 40, 50};

for (int x : arr) {
    System.out.println(x);
}

Output:

10
20
30
40
50

Yahan x ek-ek element ko represent karta hai.

x = 10
x = 20
x = 30
x = 40
x = 50
Kab use karein?

Sirf values chahiye:

for (int x : arr)

Index bhi chahiye:

for (int i = 0; i < arr.length; i++)

🔥 LeetCode mein index ki zarurat bahut hoti hai, isliye normal for loop ko strong karo.

11. Array input lena — Scanner 🔥🔥

Competitive programming/DSA mein bahut important.

import java.util.Scanner;

public class ArrayInput {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        int[] arr = new int[n];

        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        for (int i = 0; i < n; i++) {
            System.out.println(arr[i]);
        }
    }
}

Input:

5
10 20 30 40 50

Output:

10
20
30
40
50
Flow
n
↓
array create
↓
input elements
↓
traverse
↓
output
12. Sum of Array 🔥

Classic DSA problem.

int[] arr = {10, 20, 30, 40, 50};

int sum = 0;

for (int i = 0; i < arr.length; i++) {
    sum += arr[i];
}

System.out.println(sum);

Output:

150

Short form:

for (int x : arr) {
    sum += x;
}
13. Maximum element 🔥🔥

Bahut important pattern.

int[] arr = {10, 25, 7, 40, 15};

int max = arr[0];

for (int i = 1; i < arr.length; i++) {

    if (arr[i] > max) {
        max = arr[i];
    }
}

System.out.println(max);

Output:

40
Thinking
max = 10

25 > 10 → max = 25

7 > 25 → no

40 > 25 → max = 40

15 > 40 → no
14. Minimum element

Same pattern:

int[] arr = {10, 25, 7, 40, 15};

int min = arr[0];

for (int i = 1; i < arr.length; i++) {

    if (arr[i] < min) {
        min = arr[i];
    }
}

System.out.println(min);

Output:

7

🔥 Max/min pattern DSA mein extremely important hai.

15. Search an element

Linear Search:

int[] arr = {10, 20, 30, 40, 50};

int target = 30;

for (int i = 0; i < arr.length; i++) {

    if (arr[i] == target) {
        System.out.println("Found at index " + i);
        break;
    }
}

Output:

Found at index 2
16. Count an element
int[] arr = {10, 20, 10, 30, 10};

int target = 10;
int count = 0;

for (int i = 0; i < arr.length; i++) {

    if (arr[i] == target) {
        count++;
    }
}

System.out.println(count);

Output:

3

Ye frequency/counting problems ka foundation hai.

17. Even elements count karna
int[] arr = {10, 15, 20, 25, 30};

int count = 0;

for (int x : arr) {

    if (x % 2 == 0) {
        count++;
    }
}

System.out.println(count);

Output:

3
18. Array modify karna

Java arrays mutable hote hain.

int[] arr = {10, 20, 30};

arr[1] = 100;

Now:

10 100 30
19. Array reverse 🔥🔥

Two pointer pattern:

int[] arr = {1, 2, 3, 4, 5};

int left = 0;
int right = arr.length - 1;

while (left < right) {

    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;

    left++;
    right--;
}

Output array:

5 4 3 2 1

🔥 Ye pattern LeetCode mein bahut important hai.

20. Swap kaise karte hain?

Java mein:

int temp = arr[i];

arr[i] = arr[j];

arr[j] = temp;

Example:

arr = [10, 20]

i = 0
j = 1

After swap:

[20, 10]
21. Array copy

Simple copy:

int[] arr = {1, 2, 3, 4};

int[] copy = arr.clone();

Now copy contains:

[1, 2, 3, 4]

We'll later properly study:

clone()
Arrays.copyOf()
Arrays.copyOfRange()
22. Arrays class 🔥

Java mein array ke saath kaam karne ke liye:

import java.util.Arrays;
Print array

Instead of:

for (int x : arr) {
    System.out.print(x + " ");
}

you can:

System.out.println(Arrays.toString(arr));

Example:

int[] arr = {10, 20, 30};

System.out.println(Arrays.toString(arr));

Output:

[10, 20, 30]

⚠️ System.out.println(arr) mat karna. Usse actual elements normally print nahi hote.

23. Sort array 🔥🔥
import java.util.Arrays;

int[] arr = {5, 2, 8, 1, 3};

Arrays.sort(arr);

System.out.println(Arrays.toString(arr));

Output:

[1, 2, 3, 5, 8]

LeetCode mein Arrays.sort() bahut commonly useful hai.

24. Binary Search

Sorted array mein:

import java.util.Arrays;

int[] arr = {1, 3, 5, 7, 9};

int index = Arrays.binarySearch(arr, 7);

System.out.println(index);

Output:

3

⚠️ Array sorted hona important hai.

Later hum Binary Search manually bhi implement karenge, kyunki DSA mein built-in function par depend nahi karna chahiye.

25. Array Index Out of Bounds 🔥

Agar:

int[] arr = {10, 20, 30};

Valid indexes:

0
1
2

Agar:

System.out.println(arr[3]);

to error:

ArrayIndexOutOfBoundsException

Because last index:

arr.length - 1

hai.

26. Array size fixed hota hai
int[] arr = new int[5];

Is array ki length permanently:

5

hai.

Baad mein:

arr.length = 10;

❌ nahi kar sakte.

Agar dynamic size chahiye, later:

ArrayList padhenge.

27. Different data types

Array kisi bhi same data type ka ho sakta hai.

int
int[] arr = {1, 2, 3};
double
double[] arr = {1.5, 2.5, 3.5};
char
char[] arr = {'a', 'b', 'c'};
String
String[] names = {"Ram", "Shyam", "Mohan"};
28. 2D Array 🔥🔥

Ab important.

2D array basically matrix jaisa hota hai.

int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

Visual:

1 2 3
4 5 6
7 8 9

Access:

matrix[0][0] → 1
matrix[0][1] → 2
matrix[1][2] → 6
29. 2D Array traversal
for (int i = 0; i < matrix.length; i++) {

    for (int j = 0; j < matrix[i].length; j++) {

        System.out.print(matrix[i][j] + " ");
    }

    System.out.println();
}

Output:

1 2 3
4 5 6
7 8 9

🔥 Matrix LeetCode questions ke liye ye absolutely essential hai.

30. 2D array mein rows/columns
matrix.length

→ number of rows

matrix[i].length

→ current row ke columns

Ye distinction bahut important hai.

31. Jagged Array 🔥

Java mein rows ki length different ho sakti hai.

int[][] arr = {
    {1, 2},
    {3, 4, 5},
    {6}
};

Visual:

1 2
3 4 5
6

Isko jagged array kehte hain.

Isliye 2D traversal mein:

arr[i].length

use karna safe/general approach hai.

32. Array of Objects / String array

Example:

String[] names = {"Aman", "Rahul", "Bhavishya"};

for (String name : names) {
    System.out.println(name);
}

Output:

Aman
Rahul
Bhavishya
🧠 DSA ke liye Array ke CORE patterns

Ab sabse important part.

Array syntax yaad karna enough nahi hai. LeetCode mein patterns recognize karne hain.

Tumhe eventually ye patterns strong karne honge:

ARRAY
│
├── Traversal
├── Sum / Count
├── Min / Max
├── Linear Search
├── Frequency
├── Reverse
├── Swap
│
├── Two Pointer
├── Sliding Window
├── Prefix Sum
├── Difference Array
├── Kadane's Algorithm
├── Sorting
├── Binary Search
├── Hashing + Array
│
├── Subarray
├── Subsequence
├── Pair / Triplet
├── Merge Arrays
│
├── 2D Array / Matrix
├── Matrix Traversal
├── Spiral Matrix
├── Rotate Matrix
│
└── Advanced Array Problems

Ye poora array DSA universe hai, aur hum inhe one-by-one karenge.

⚡ Complexity Basics

Normal traversal:

for (int i = 0; i < n; i++)

Time:

O(n)

Space:

O(1)

Max/min:

O(n) time.

Linear search:

O(n) worst case.

Reverse:

O(n) time, O(1) extra space.

Sorting:

Arrays.sort(arr);

typically O(n log n) for primitive arrays.

🎯 LeetCode ke liye tumhe kya aana chahiye?

Agar ye foundation strong hai, to language side se tum ye type ke questions start kar sakte ho:

Two Sum
Best Time to Buy and Sell Stock
Contains Duplicate
Maximum Subarray
Move Zeroes
Remove Duplicates from Sorted Array
Merge Sorted Array
Rotate Array
Majority Element
Sort Colors
Product of Array Except Self
3Sum
Container With Most Water
Subarray Sum
Spiral Matrix
Rotate Image

Aur phir advanced:

Sliding Window
Prefix Sum + HashMap
Binary Search on Array
Monotonic techniques
Greedy + Array
DP + Array
🔥 Abhi ek important rule

Abhi saare patterns ek saath mat padhna.

Pehle Java mein ye basic syntax haath mein lao:

int[] arr
arr[i]
arr.length

for loop
for-each loop

input using Scanner

max/min
sum
search
count

swap
reverse

Arrays.toString()
Arrays.sort()

Uske baad hum Array DSA patterns start karenge:

Traversal → Two Pointer → Sliding Window → Prefix Sum → Kadane → Binary Search → Subarray → Matrix → Advanced.

Aur har pattern ke baad Java mein actual LeetCode questions karenge, taaki tumhe sirf syntax nahi balki question dekhkar "isme kaunsa pattern lagega?" ye samajh aaye.