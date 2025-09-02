## 🔹 Problem: Find the Row with Maximum Number of 1s

We are given a **binary matrix** (only 0s and 1s) where **each row is sorted** (all 0’s before 1’s).
We need to find the **row index with the maximum number of 1’s**.

---

## 🔹 Approaches

### **1. Brute Force**

* Traverse every row.
* Count the number of `1`s using a loop.
* Track the row with the maximum count.

⏱ **Time Complexity:** O(n × m)
📦 **Space Complexity:** O(1)

---

### **2. Binary Search per Row (Optimized)**

* Since each row is sorted:

  * Use **binary search** to find the first `1` in a row.
  * The count of `1`s = (m - index\_of\_first\_1).
* Compare counts across rows.

⏱ **Time Complexity:** O(n log m)
📦 **Space Complexity:** O(1)

---

### **3. Super Optimized (O(n + m))**

* Start from the **top-right corner** of the matrix.
* If we see a `1`, move **left** (more 1’s in this row).
* If we see a `0`, move **down** (fewer 1’s in this row).
* Keep track of the row index with the most 1’s.

⏱ **Time Complexity:** O(n + m)
📦 **Space Complexity:** O(1)

---

## 🔹 Java Code (All 3 Approaches)

```java
public class MaxOnesRow {

    // Brute Force O(n*m)
    public static int rowWithMaxOnesBrute(int[][] mat) {
        int n = mat.length, m = mat[0].length;
        int maxRow = -1, maxCount = 0;

        for (int i = 0; i < n; i++) {
            int count = 0;
            for (int j = 0; j < m; j++) {
                if (mat[i][j] == 1) count++;
            }
            if (count > maxCount) {
                maxCount = count;
                maxRow = i;
            }
        }
        return maxRow;
    }

    // Binary Search per row O(n log m)
    public static int rowWithMaxOnesBinary(int[][] mat) {
        int n = mat.length, m = mat[0].length;
        int maxRow = -1, maxCount = 0;

        for (int i = 0; i < n; i++) {
            int index = firstOneIndex(mat[i]);
            int count = (index == -1) ? 0 : (m - index);

            if (count > maxCount) {
                maxCount = count;
                maxRow = i;
            }
        }
        return maxRow;
    }

    private static int firstOneIndex(int[] row) {
        int low = 0, high = row.length - 1, ans = -1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (row[mid] == 1) {
                ans = mid;
                high = mid - 1; // move left
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }

    // Optimized O(n+m)
    public static int rowWithMaxOnesOptimized(int[][] mat) {
        int n = mat.length, m = mat[0].length;
        int j = m - 1, maxRow = -1;

        for (int i = 0; i < n; i++) {
            while (j >= 0 && mat[i][j] == 1) {
                maxRow = i;
                j--; // move left
            }
        }
        return maxRow;
    }

    public static void main(String[] args) {
        int[][] mat = {
            {0, 0, 0, 1},
            {0, 1, 1, 1},
            {0, 0, 1, 1},
            {1, 1, 1, 1}
        };

        System.out.println("Brute Force: " + rowWithMaxOnesBrute(mat));
        System.out.println("Binary Search: " + rowWithMaxOnesBinary(mat));
        System.out.println("Optimized: " + rowWithMaxOnesOptimized(mat));
    }
}
```

---

✅ **Output (for given matrix):**

```
Brute Force: 3
Binary Search: 3
Optimized: 3
```

---

Would you like me to also prepare a **step-by-step dry run with diagram** (like how we did earlier) for the **O(n+m) optimized solution**?
