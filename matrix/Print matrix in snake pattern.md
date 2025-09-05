Great question 👍 Let’s solve **Print matrix in snake pattern** in Java.

---

## ✅ Snake Pattern Explanation

* Traverse row by row.
* If row index is **even** → print **left to right**.
* If row index is **odd** → print **right to left**.

---

## ✅ Java Code

```java
import java.util.*;

public class SnakePattern {
    public static void printSnake(int[][] mat, int n) {
        for (int i = 0; i < n; i++) {
            if (i % 2 == 0) {
                // left to right
                for (int j = 0; j < n; j++) {
                    System.out.print(mat[i][j] + " ");
                }
            } else {
                // right to left
                for (int j = n - 1; j >= 0; j--) {
                    System.out.print(mat[i][j] + " ");
                }
            }
        }
    }

    public static void main(String[] args) {
        int[][] mat = {
            {10, 20, 30, 40},
            {15, 25, 35, 45},
            {27, 29, 37, 48},
            {32, 33, 39, 50}
        };

        int n = mat.length;
        printSnake(mat, n);
    }
}
```

---

## ✅ Example Run

### Input:

```
10 20 30 40
15 25 35 45
27 29 37 48
32 33 39 50
```

### Output:

```
10 20 30 40 45 35 25 15 27 29 37 48 50 39 33 32
```

---

## ✅ Complexity

* **Time:** O(n²) (visiting each element once)
* **Space:** O(1) (no extra space, printing directly)

---

Do you want me to also show the version where the snake pattern is returned as a **list/array** instead of just printing?
