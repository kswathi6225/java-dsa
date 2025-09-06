Perfect 🚀 I’ll give you **Java code for all 8 basic matrix problems** with sample **input and output** so you can practice.

---

## 1️⃣ Print a Matrix

```java
public class PrintMatrix {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        System.out.println("Matrix:");
        for (int i = 0; i < mat.length; i++) {
            for (int j = 0; j < mat[0].length; j++) {
                System.out.print(mat[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

✅ Output:

```
Matrix:
1 2 3
4 5 6
7 8 9
```

---

## 2️⃣ Transpose of a Matrix

```java
public class TransposeMatrix {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3},
            {4, 5, 6}
        };

        int rows = mat.length, cols = mat[0].length;
        int[][] transpose = new int[cols][rows];

        for (int i = 0; i < rows; i++) {
            for (int j = 0; j < cols; j++) {
                transpose[j][i] = mat[i][j];
            }
        }

        System.out.println("Transpose:");
        for (int i = 0; i < cols; i++) {
            for (int j = 0; j < rows; j++) {
                System.out.print(transpose[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

✅ Output:

```
Transpose:
1 4
2 5
3 6
```

---

## 3️⃣ Sum of Rows and Columns

```java
public class SumRowsCols {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int rows = mat.length, cols = mat[0].length;

        // Row sums
        for (int i = 0; i < rows; i++) {
            int sum = 0;
            for (int j = 0; j < cols; j++) sum += mat[i][j];
            System.out.println("Sum of row " + (i+1) + " = " + sum);
        }

        // Column sums
        for (int j = 0; j < cols; j++) {
            int sum = 0;
            for (int i = 0; i < rows; i++) sum += mat[i][j];
            System.out.println("Sum of col " + (j+1) + " = " + sum);
        }
    }
}
```

✅ Output:

```
Sum of row 1 = 6
Sum of row 2 = 15
Sum of row 3 = 24
Sum of col 1 = 12
Sum of col 2 = 15
Sum of col 3 = 18
```

---

## 4️⃣ Diagonal Sum

```java
public class DiagonalSum {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int n = mat.length;
        int primary = 0, secondary = 0;

        for (int i = 0; i < n; i++) {
            primary += mat[i][i];
            secondary += mat[i][n - i - 1];
        }

        System.out.println("Primary diagonal sum = " + primary);
        System.out.println("Secondary diagonal sum = " + secondary);
    }
}
```

✅ Output:

```
Primary diagonal sum = 15
Secondary diagonal sum = 15
```

---

## 5️⃣ Search in a Matrix

```java
public class SearchMatrix {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int target = 5;
        boolean found = false;

        for (int i = 0; i < mat.length; i++) {
            for (int j = 0; j < mat[0].length; j++) {
                if (mat[i][j] == target) {
                    System.out.println("Found at (" + i + ", " + j + ")");
                    found = true;
                }
            }
        }

        if (!found) System.out.println("Not Found");
    }
}
```

✅ Output:

```
Found at (1, 1)
```

---

## 6️⃣ Identity Matrix Check

```java
public class IdentityMatrix {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 0, 0},
            {0, 1, 0},
            {0, 0, 1}
        };

        boolean isIdentity = true;
        int n = mat.length;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if ((i == j && mat[i][j] != 1) || (i != j && mat[i][j] != 0)) {
                    isIdentity = false;
                }
            }
        }

        System.out.println("Is Identity Matrix? " + isIdentity);
    }
}
```

✅ Output:

```
Is Identity Matrix? true
```

---

## 7️⃣ Maximum Element in Matrix

```java
public class MaxInMatrix {
    public static void main(String[] args) {
        int[][] mat = {
            {5, 8, 2},
            {9, 3, 7},
            {1, 6, 4}
        };

        int max = Integer.MIN_VALUE;
        for (int i = 0; i < mat.length; i++) {
            for (int j = 0; j < mat[0].length; j++) {
                max = Math.max(max, mat[i][j]);
            }
        }

        System.out.println("Maximum element = " + max);
    }
}
```

✅ Output:

```
Maximum element = 9
```

---

## 8️⃣ Snake Pattern Traversal

```java
public class SnakePattern {
    public static void main(String[] args) {
        int[][] mat = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int rows = mat.length, cols = mat[0].length;

        for (int i = 0; i < rows; i++) {
            if (i % 2 == 0) { // left to right
                for (int j = 0; j < cols; j++) System.out.print(mat[i][j] + " ");
            } else { // right to left
                for (int j = cols - 1; j >= 0; j--) System.out.print(mat[i][j] + " ");
            }
        }
    }
}
```

✅ Output:

```
1 2 3 6 5 4 7 8 9
```

---

✨ That’s **8 beginner-friendly matrix problems with Java code + input/output**.
Do you want me to next move to **medium-level matrix problems** (like spiral traversal, rotate matrix, boundary traversal), or should we first do **more easy ones**?
