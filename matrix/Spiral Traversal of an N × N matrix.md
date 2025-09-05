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

Would you like me to also show you the **version that prints directly (without using extra list)** to save space?
