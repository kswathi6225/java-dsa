
## 🔹 Problem: Search in 2D Matrix

You are given an `m x n` matrix, where each row is sorted in ascending order, and the first element of each row is greater than the last element of the previous row.
Find if a target exists in the matrix.

---

## ✅ Approach 1: Brute Force

* Traverse all elements.
* **Time:** O(m × n)
* **Space:** O(1)

---

## ✅ Approach 2: Binary Search on Whole Matrix

Since the 2D matrix is sorted like a **flattened sorted array**:

* Treat the matrix as an array of size `m*n`.
* Index mapping:

  * `row = mid / n`
  * `col = mid % n`
* Apply binary search.

**Time:** O(log(m × n))
**Space:** O(1)

---

## ✅ Java Code (Binary Search Approach)

```java
public class Search2DMatrix {
    public static boolean searchMatrix(int[][] matrix, int target) {
        int m = matrix.length;        // number of rows
        int n = matrix[0].length;     // number of columns

        int low = 0, high = m * n - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2;
            int row = mid / n;
            int col = mid % n;

            if (matrix[row][col] == target) {
                return true;
            } else if (matrix[row][col] < target) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }

        return false;
    }

    public static void main(String[] args) {
        int[][] matrix = {
            {1, 3, 5, 7},
            {10, 11, 16, 20},
            {23, 30, 34, 60}
        };
        int target = 3;
        System.out.println(searchMatrix(matrix, target)); // true
    }
}
```

---

## ✅ Approach 3: Binary Search Row + Column

1. First find the possible row using binary search on the **first column**.
2. Then perform binary search in that row.

**Time:** O(log m + log n)
**Space:** O(1)

---

👉 Do you want me to also give code for **Search in a Row & Column-wise Sorted Matrix** (different from this one, where each row and column is individually sorted, but not globally sorted)?
