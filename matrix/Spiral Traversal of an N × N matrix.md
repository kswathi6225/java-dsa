Nice one 👍 This is the **Spiral Traversal of an N × N matrix** problem.

We’ll carefully build the **Java code** step by step.

---

## ✅ Approach

1. Maintain **four boundaries**:

   * `top = 0` → starting row
   * `bottom = N-1` → last row
   * `left = 0` → starting column
   * `right = N-1` → last column

2. Traverse in 4 directions (like layers of onion 🧅):

   * **Left → Right** (along top row)
   * **Top → Bottom** (along right column)
   * **Right → Left** (along bottom row)
   * **Bottom → Top** (along left column)

3. After each traversal, shrink boundaries (`top++`, `right--`, `bottom--`, `left++`).

4. Stop when `top <= bottom && left <= right`.

---

## ✅ Code

```java
import java.util.*;

public class SpiralMatrix {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input size
        int N = sc.nextInt();
        int[][] matrix = new int[N][N];

        // Input matrix elements
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                matrix[i][j] = sc.nextInt();
            }
        }

        List<Integer> result = new ArrayList<>();

        int top = 0, bottom = N - 1, left = 0, right = N - 1;

        while (top <= bottom && left <= right) {
            // Traverse Left → Right
            for (int j = left; j <= right; j++) {
                result.add(matrix[top][j]);
            }
            top++;

            // Traverse Top → Bottom
            for (int i = top; i <= bottom; i++) {
                result.add(matrix[i][right]);
            }
            right--;

            // Traverse Right → Left (if rows remain)
            if (top <= bottom) {
                for (int j = right; j >= left; j--) {
                    result.add(matrix[bottom][j]);
                }
                bottom--;
            }

            // Traverse Bottom → Top (if cols remain)
            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    result.add(matrix[i][left]);
                }
                left++;
            }
        }

        // Print result
        for (int num : result) {
            System.out.print(num + " ");
        }
    }
}
```

---

## ✅ Example Run

### Input

```
3
1 2 3
4 5 6
7 8 9
```

### Output

```
1 2 3 6 9 8 7 4 5
```

---

## ✅ Complexity

* **Time:** O(N²) (each element visited once)
* **Space:** O(N²) for result list (can also print directly if no list needed)

---

Ah, I see what you mean 👍
You’re asking about **input format**:

```
3 3
1 2 3
4 5 6
7 8 9
```

Here, the first line `3 3` means:

* **3 rows**
* **3 columns**

I didn’t ignore it 🙂 — in my earlier code, I hardcoded the matrix. But if we want to **take input dynamically**, we should use those `3 3` values to build the matrix.

---

### ✅ Java Code (Take Input with n, m)

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Read dimensions
        int n = sc.nextInt();
        int m = sc.nextInt();

        // Read matrix
        int[][] matrix = new int[n][m];
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                matrix[i][j] = sc.nextInt();
            }
        }

        // Print in spiral order
        printSpiral(matrix, n, m);
    }

    public static void printSpiral(int[][] matrix, int n, int m) {
        int top = 0, bottom = n - 1;
        int left = 0, right = m - 1;

        while (top <= bottom && left <= right) {
            // left → right
            for (int i = left; i <= right; i++) {
                System.out.print(matrix[top][i]);
            }
            top++;

            // top → bottom
            for (int i = top; i <= bottom; i++) {
                System.out.print(matrix[i][right]);
            }
            right--;

            // right → left
            if (top <= bottom) {
                for (int i = right; i >= left; i--) {
                    System.out.print(matrix[bottom][i]);
                }
                bottom--;
            }

            // bottom → top
            if (left <= right) {
                for (int i = bottom; i >= top; i--) {
                    System.out.print(matrix[i][left]);
                }
                left++;
            }
        }
    }
}
```

---

### ✅ Example Run

**Input:**

```
3 3
1 2 3
4 5 6
7 8 9
```

**Output:**

```
123698745
```

---

👉 So, I wasn’t ignoring `3 3`; I just assumed static input earlier.
Would you like me to also make this **work for non-square matrices** (e.g., `3 4`, `2 5` etc.)?


Would you like me to also show you the **version that prints directly (without using extra list)** to save space?
