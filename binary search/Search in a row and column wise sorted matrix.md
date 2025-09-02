Great question 👍
Yes, this is one of the **most important binary search-based problems**:

---

## 🔹 Problem: Search in a row and column wise sorted matrix

You’re given a matrix where:

* Each row is sorted in increasing order.
* Each column is sorted in increasing order.

You need to search for a target element efficiently.

---

## 🔹 Approaches

### 1. **Brute Force (O(N×M))**

* Traverse every element in the matrix.
* Compare with the target.
  ❌ Not efficient.

---

### 2. **Binary Search on each row (O(N log M))**

* Apply binary search on every row.
* Works fine, but can be optimized.

---

### 3. **Optimized Staircase Search (O(N + M))** ✅

* Start from **top-right corner** of the matrix.
* If `matrix[row][col] == target`, return true.
* If `matrix[row][col] > target`, move left (col--)
* If `matrix[row][col] < target`, move down (row++)
* If we go out of bounds, target not found.

👉 This is the **best approach**.

---

## 🔹 Java Code (Optimized O(N+M))

```java
public class SearchInMatrix {
    public static boolean searchMatrix(int[][] matrix, int target) {
        int n = matrix.length;
        int m = matrix[0].length;

        int row = 0, col = m - 1;  // start from top-right

        while (row < n && col >= 0) {
            if (matrix[row][col] == target) {
                return true; // found
            } else if (matrix[row][col] > target) {
                col--; // move left
            } else {
                row++; // move down
            }
        }
        return false; // not found
    }

    public static void main(String[] args) {
        int[][] matrix = {
            {1, 4, 7, 11},
            {2, 5, 8, 12},
            {3, 6, 9, 16},
            {10, 13, 14, 17}
        };

        int target = 5;
        if (searchMatrix(matrix, target)) {
            System.out.println("Element found");
        } else {
            System.out.println("Element not found");
        }
    }
}
```

---

## 🔹 Time & Space Complexity

* **Time:** `O(N + M)`
* **Space:** `O(1)`

---

⚡ This is an **Amazon/Microsoft/Google favorite** interview problem.

Would you like me to also cover the **LeetCode variation (Search a 2D Matrix - where the whole matrix is sorted like a 1D array)**?
