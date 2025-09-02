Great question 👍.
"Find Peak Element in a 2D Matrix" is a classic interview problem. Let’s go step by step with **different approaches**, their **time/space complexities**, and **Java code**.

---

## 🔹 Problem Statement

A **peak element in a 2D matrix** is an element that is **not smaller than its neighbors** (top, bottom, left, right).
We need to **find any one peak**.

---

## **Approach 1: Brute Force**

* Traverse every cell and check if it is greater than or equal to its valid neighbors.
* If yes → return it as a peak.

### Complexity

* **Time**: O(m × n) (check every element)
* **Space**: O(1)

### Code

```java
public class Peak2DBruteForce {
    public static int[] findPeak(int[][] mat) {
        int m = mat.length, n = mat[0].length;

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                boolean up = (i == 0) || (mat[i][j] >= mat[i-1][j]);
                boolean down = (i == m-1) || (mat[i][j] >= mat[i+1][j]);
                boolean left = (j == 0) || (mat[i][j] >= mat[i][j-1]);
                boolean right = (j == n-1) || (mat[i][j] >= mat[i][j+1]);

                if (up && down && left && right) {
                    return new int[]{i, j}; // Peak found
                }
            }
        }
        return new int[]{-1, -1}; // No peak
    }

    public static void main(String[] args) {
        int[][] mat = {
            {10, 8, 10, 10},
            {14, 13, 12, 11},
            {15, 9, 11, 21},
            {16, 17, 19, 20}
        };

        int[] peak = findPeak(mat);
        System.out.println("Peak at: (" + peak[0] + "," + peak[1] + ")");
    }
}
```

---

## **Approach 2: Row-wise Peak Search (Greedy)**

* Look for the **maximum in each row**, then check if it's a peak.
* If not, move up/down depending on neighbors.

### Complexity

* **Time**: O(m × n) in worst case (still not efficient).
* **Space**: O(1).

---

## **Approach 3: Binary Search on Columns (Optimized ✅)**

👉 The **optimal method** used in interviews.

### Idea

1. Pick the **middle column**.
2. Find the **global maximum element** in that column.
3. Compare it with neighbors (left & right).

   * If it’s a peak → return it.
   * If the left neighbor is bigger → move left (search left half).
   * If the right neighbor is bigger → move right (search right half).
4. Repeat using **binary search** on columns.

### Complexity

* **Time**: O(m × log n) (binary search on columns, scanning each col O(m))
* **Space**: O(1)

### Code

```java
public class Peak2DBinarySearch {
    public static int[] findPeakGrid(int[][] mat) {
        int m = mat.length, n = mat[0].length;

        int left = 0, right = n - 1;
        while (left <= right) {
            int mid = (left + right) / 2;

            // Find global max in mid column
            int maxRow = 0;
            for (int i = 0; i < m; i++) {
                if (mat[i][mid] > mat[maxRow][mid]) {
                    maxRow = i;
                }
            }

            int leftNeighbor = (mid - 1 >= 0) ? mat[maxRow][mid - 1] : -1;
            int rightNeighbor = (mid + 1 < n) ? mat[maxRow][mid + 1] : -1;

            // Check if it's a peak
            if (mat[maxRow][mid] >= leftNeighbor && mat[maxRow][mid] >= rightNeighbor) {
                return new int[]{maxRow, mid};
            }

            // Move left or right
            if (leftNeighbor > mat[maxRow][mid]) {
                right = mid - 1;
            } else {
                left = mid + 1;
            }
        }

        return new int[]{-1, -1}; // No peak
    }

    public static void main(String[] args) {
        int[][] mat = {
            {10, 8, 10, 10},
            {14, 13, 12, 11},
            {15, 9, 11, 21},
            {16, 17, 19, 20}
        };

        int[] peak = findPeakGrid(mat);
        System.out.println("Peak at: (" + peak[0] + "," + peak[1] + ")");
    }
}
```

---

## ✅ Summary of Approaches

| Approach                | Time Complexity  | Space | Notes                   |
| ----------------------- | ---------------- | ----- | ----------------------- |
| Brute Force             | O(m × n)         | O(1)  | Simple but slow         |
| Row-wise Search         | O(m × n)         | O(1)  | Slightly greedy         |
| Binary Search (Optimal) | **O(m × log n)** | O(1)  | Best for large matrices |

---

👉 Do you want me to also explain this **with a step-by-step diagram** (like how mid column moves left/right)?
