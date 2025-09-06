Got it 👍 Let’s do **matrix addition and subtraction** in Java.
We’ll assume both matrices are of the **same size** (rows × cols).

---

## ➕ Matrix Addition

```java
public class MatrixAddition {
    public static void main(String[] args) {
        int[][] A = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int[][] B = {
            {9, 8, 7},
            {6, 5, 4},
            {3, 2, 1}
        };

        int rows = A.length, cols = A[0].length;
        int[][] sum = new int[rows][cols];

        // Add matrices
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                sum[i][j] = A[i][j] + B[i][j];
            }
        }

        // Print result
        System.out.println("Matrix Addition:");
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                System.out.print(sum[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

✅ **Output:**

```
Matrix Addition:
10 10 10
10 10 10
10 10 10
```

---

## ➖ Matrix Subtraction

```java
public class MatrixSubtraction {
    public static void main(String[] args) {
        int[][] A = {
            {5, 6, 7},
            {8, 9, 10},
            {11, 12, 13}
        };

        int[][] B = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int rows = A.length, cols = A[0].length;
        int[][] diff = new int[rows][cols];

        // Subtract matrices
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                diff[i][j] = A[i][j] - B[i][j];
            }
        }

        // Print result
        System.out.println("Matrix Subtraction:");
        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                System.out.print(diff[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

✅ **Output:**

```
Matrix Subtraction:
4 4 4
4 4 4
4 4 4
```

---

👉 Do you also want me to give you **matrix multiplication code** (a very common interview problem), or should I stick only to addition/subtraction for now?
