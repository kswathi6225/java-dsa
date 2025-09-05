Nice one 👍 Checking whether a matrix is a **Magic Square** is a common interview-style problem.

---

## 🔹 What is a Magic Square?

A square matrix of size $n \times n$ is a **magic square** if:

1. The sum of every **row** is the same.
2. The sum of every **column** is the same.
3. The sum of the two **main diagonals** is also the same.

This common sum is called the **magic constant**.

👉 Formula for magic constant (if numbers are 1 to $n^2$):

$$
M = \frac{n \times (n^2+1)}{2}
$$

---

## ✅ Java Code

```java
import java.util.*;

public class MagicSquareCheck {
    public static boolean isMagicSquare(int[][] mat) {
        int n = mat.length;

        // Step 1: Calculate the sum of the first row (reference sum)
        int sum = 0;
        for (int j = 0; j < n; j++) {
            sum += mat[0][j];
        }

        // Step 2: Check sums of all rows
        for (int i = 1; i < n; i++) {
            int rowSum = 0;
            for (int j = 0; j < n; j++) {
                rowSum += mat[i][j];
            }
            if (rowSum != sum) return false;
        }

        // Step 3: Check sums of all columns
        for (int j = 0; j < n; j++) {
            int colSum = 0;
            for (int i = 0; i < n; i++) {
                colSum += mat[i][j];
            }
            if (colSum != sum) return false;
        }

        // Step 4: Check main diagonal
        int diag1 = 0, diag2 = 0;
        for (int i = 0; i < n; i++) {
            diag1 += mat[i][i];           // main diagonal
            diag2 += mat[i][n - i - 1];   // secondary diagonal
        }
        if (diag1 != sum || diag2 != sum) return false;

        return true;
    }

    public static void main(String[] args) {
        int[][] mat = {
            {2, 7, 6},
            {9, 5, 1},
            {4, 3, 8}
        };

        if (isMagicSquare(mat)) {
            System.out.println("Yes, it is a Magic Square!");
        } else {
            System.out.println("No, it is NOT a Magic Square.");
        }
    }
}
```

---

## ✅ Example Run

### Input:

```
2 7 6
9 5 1
4 3 8
```

### Output:

```
Yes, it is a Magic Square!
```

---

## ✅ Complexity

* **Time:** O(n²) (check every element once)
* **Space:** O(1)

---

Do you want me to also add a **check for distinct numbers from 1 to n²** (which is required in some definitions of Magic Square)?
