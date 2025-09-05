Perfect 👍 Let’s write the **Java program for Matrix Multiplication** step by step.

---

## ✅ Rules Recap

* If `matrix1` is of order **a × b** and `matrix2` is of order **b × c**,
  → Resultant matrix will be of order **a × c**.
* Formula:

$$
result[i][j] = \sum_{k=0}^{b-1} matrix1[i][k] \times matrix2[k][j]
$$

---

## ✅ Java Code

```java
import java.util.*;

public class MatrixMultiplication {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input dimensions of first matrix
        System.out.print("Enter rows of first matrix: ");
        int a = sc.nextInt();
        System.out.print("Enter columns of first matrix: ");
        int b = sc.nextInt();

        // Input dimensions of second matrix
        System.out.print("Enter rows of second matrix: ");
        int b2 = sc.nextInt();
        System.out.print("Enter columns of second matrix: ");
        int c = sc.nextInt();

        // Check compatibility (cols of 1st = rows of 2nd)
        if (b != b2) {
            System.out.println("Matrix multiplication not possible!");
            return;
        }

        // Input first matrix
        int[][] matrix1 = new int[a][b];
        System.out.println("Enter elements of first matrix:");
        for (int i = 0; i < a; i++) {
            for (int j = 0; j < b; j++) {
                matrix1[i][j] = sc.nextInt();
            }
        }

        // Input second matrix
        int[][] matrix2 = new int[b2][c];
        System.out.println("Enter elements of second matrix:");
        for (int i = 0; i < b2; i++) {
            for (int j = 0; j < c; j++) {
                matrix2[i][j] = sc.nextInt();
            }
        }

        // Resultant matrix of size a × c
        int[][] result = new int[a][c];

        // Matrix multiplication
        for (int i = 0; i < a; i++) {
            for (int j = 0; j < c; j++) {
                result[i][j] = 0;
                for (int k = 0; k < b; k++) {
                    result[i][j] += matrix1[i][k] * matrix2[k][j];
                }
            }
        }

        // Print resultant matrix
        System.out.println("Resultant Matrix:");
        for (int i = 0; i < a; i++) {
            for (int j = 0; j < c; j++) {
                System.out.print(result[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

---

## ✅ Example Run

### Input

```
First Matrix (4×3):
1 1 1
2 2 2
3 3 3
4 4 4

Second Matrix (3×4):
1 1 1 1
2 2 2 2
3 3 3 3
```

### Output

```
Resultant Matrix:
6 6 6 6
12 12 12 12
18 18 18 18
24 24 24 24
```

---

## ✅ Complexity

* **Time Complexity:** O(a × b × c) (triple loop)
* **Space Complexity:** O(a × c) (result matrix)

---

Do you want me to also give you a **version that handles rectangular matrices (not just square ones)** with generic input and printing?
