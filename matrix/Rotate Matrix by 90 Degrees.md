# 🔄 Rotate Matrix by 90 Degrees

We’ll assume **square matrix (n × n)**.

Example Input:

```
Matrix = 
1 2 3
4 5 6
7 8 9
```

Expected Output (after 90° clockwise):

```
7 4 1
8 5 2
9 6 3
```

---

## ✅ Approach 1: Using Extra Space (Naive)

* Create a new matrix.
* Place element `(i, j)` → `(j, n-1-i)`.

### **Java Code**

```java
import java.util.*;

public class RotateMatrixExtraSpace {
    static int[][] rotate(int[][] matrix) {
        int n = matrix.length;
        int[][] res = new int[n][n];

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                res[j][n - 1 - i] = matrix[i][j];
            }
        }
        return res;
    }

    public static void main(String[] args) {
        int[][] matrix = {{1,2,3},{4,5,6},{7,8,9}};
        int[][] rotated = rotate(matrix);

        for (int[] row : rotated) {
            System.out.println(Arrays.toString(row));
        }
    }
}
```

### **Output**

```
[7, 4, 1]
[8, 5, 2]
[9, 6, 3]
```

### **Complexity**

* **Time:** `O(n²)`
* **Space:** `O(n²)` (extra matrix)

---

## ✅ Approach 2: Transpose + Reverse Each Row (In-place, most common)

Steps:

1. **Transpose** → convert rows → columns.
2. **Reverse each row**.

### **Java Code**

```java
import java.util.*;

public class RotateMatrixInPlace {
    static void rotate(int[][] matrix) {
        int n = matrix.length;

        // Step 1: Transpose
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        // Step 2: Reverse each row
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n / 2; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[i][n - 1 - j];
                matrix[i][n - 1 - j] = temp;
            }
        }
    }

    public static void main(String[] args) {
        int[][] matrix = {{1,2,3},{4,5,6},{7,8,9}};
        rotate(matrix);

        for (int[] row : matrix) {
            System.out.println(Arrays.toString(row));
        }
    }
}
```

### **Output**

```
[7, 4, 1]
[8, 5, 2]
[9, 6, 3]
```

### **Complexity**

* **Time:** `O(n²)`
* **Space:** `O(1)` (in-place)

---

# ⚡ Summary

| Approach            | Space   | Time    | Notes                             |
| ------------------- | ------- | ------- | --------------------------------- |
| Extra Matrix        | `O(n²)` | `O(n²)` | Easiest, but not memory efficient |
| Transpose + Reverse | `O(1)`  | `O(n²)` | ✅ Most popular, clean            |

---

👉 Do you also want me to give the **anti-clockwise 90° rotation** versions as well (same 3 approaches but reversed order)?
