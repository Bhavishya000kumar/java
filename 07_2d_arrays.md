# Chapter 7 — 2D Arrays ⭐⭐

### 1. What is it?
A 2D array is an array of arrays. In memory, it represents a grid (matrix) consisting of rows and columns. In Java, it is structured as an array pointing to other 1D arrays representing rows.

### 2. Why do I need it for placements?
Grid-based coding questions are extremely common in assessments. Algorithms like Matrix Rotation (Rotate 90 degrees), Transpose, and Spiral Traversal are standard questions in recruiter exams (Accenture, Capgemini).

### 3. C++ → Java Comparison
*   **Initialization:**
    *   C++: `int matrix[3][4];`
    *   Java: `int[][] matrix = new int[3][4];`
*   **Accessing Dimensions:**
    *   C++: Dimensions are hardcoded or passed separately (e.g. `R` and `C`).
    *   Java: Number of rows = `matrix.length`. Number of columns in row `i` = `matrix[i].length`.
*   **Jagged Arrays:**
    *   C++: Cannot easily have rows of different lengths statically.
    *   Java: Naturally supports jagged arrays because each row reference can point to a 1D array of a different size.

### 4. C++ Syntax/Example
```cpp
#include <iostream>
using namespace std;

int main() {
    int matrix[2][3] = {{1, 2, 3}, {4, 5, 6}};
    int rows = 2;
    int cols = 3;
    
    for(int i = 0; i < rows; i++) {
        for(int j = 0; j < cols; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}
```

### 5. Java Equivalent Syntax/Example
```java
public class Main {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6}
        };
        int rows = matrix.length;
        
        for (int i = 0; i < rows; i++) {
            int cols = matrix[i].length;
            for (int j = 0; j < cols; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

### 6. Important Java Differences
*   **Memory Structure:** In Java, `matrix` points to a 1D array of references of size `rows`. Each index of this array points to a separate 1D array of size `cols` allocated somewhere else in the heap.
*   **Jagged Arrays Initialization:** You can declare a 2D array without defining the column size:
    ```java
    int[][] jagged = new int[3][];
    jagged[0] = new int[2]; // row 0 has 2 cols
    jagged[1] = new int[4]; // row 1 has 4 cols
    jagged[2] = new int[3]; // row 2 has 3 cols
    ```

### 7. Simple Hinglish Explanation
C++ mein array memory contiguous linear sequence mein store hoti hai. Par Java mein `matrix` aasal mein ek arrays-ka-array hota hai. `matrix.length` aapko total rows dega. Kisi particular row `i` ke andar kitne columns hain, woh nikalne ke liye aap `matrix[i].length` likhoge.
Is structure ki wajah se Java mein *Jagged Arrays* banana asan hai (jismein har row ki length alag-alag ho sakti hai).

### 8. Small Practical Examples
Let's see Matrix Transpose (swapping `matrix[i][j]` with `matrix[j][i]`).
```java
public class Main {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        int n = matrix.length;
        
        // Transpose in-place (assuming square matrix)
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }
        
        // Print transposed matrix
        for (int[] row : matrix) {
            for (int val : row) {
                System.out.print(val + " ");
            }
            System.out.println();
        }
    }
}
```

### 9. Expected Output
```text
1 4 7 
2 5 8 
3 6 9 
```

### 10. Common Mistakes
*   **Hardcoding Column Length:** Writing `for (int j = 0; j < cols; j++)` where `cols` is static, which fails if the matrix is jagged. Always use `matrix[i].length`.
*   **NullPointer Exception:** Accessing `matrix[i][j]` on a row that hasn't been initialized (e.g. `matrix[i] = null`).

### 11. Interview Point
*   **How does memory layout of 2D array differ in C++ vs Java?**
    In C++, a 2D array is stored contiguously (Row-major order). In Java, a 2D array is an array of objects where each row is a separate object reference pointing to a different location on the heap.

### 12. Coding-Platform Usage
In problems like "Rotate Image" (rotate matrix 90 degrees clockwise), the standard recipe is:
1. Transpose the matrix.
2. Reverse each row.
Here is the helper code to reverse a row in Java:
```java
public void reverseRow(int[] row) {
    int start = 0, end = row.length - 1;
    while (start < end) {
        int temp = row[start];
        row[start] = row[end];
        row[end] = temp;
        start++;
        end--;
    }
}
```

### 13. Quick Revision
*   Declare: `int[][] matrix = new int[rows][cols];`
*   Row Count: `matrix.length`
*   Column Count (Row `i`): `matrix[i].length`
*   Jagged initialization: `int[][] jagged = new int[3][]; jagged[0] = new int[5];`
