Great question 👍 — **Matrix Median** is a classic **Binary Search on Answer** problem.

We’re given a **row-wise sorted matrix** (each row is sorted, but the whole matrix may not be). We need to find the **median of all elements**.

---

## 🔹 Problem Example

Matrix:

```
1  3  5
2  6  9
3  6  9
```

All elements sorted: `[1, 2, 3, 3, 5, 6, 6, 9, 9]`
Median = `5` (middle element, index = 4 in 0-based indexing).

---

## 🔹 Approaches

### **Approach 1: Flatten & Sort**

1. Extract all elements into a list.
2. Sort the list.
3. Pick the middle element.

* **Time:** `O(R * C log(R * C))`
* **Space:** `O(R * C)`

---

### **Approach 2: Min-Heap / Max-Heap**

* Push all elements into a heap and extract until the middle.

* Slightly better than full sort in some cases, but not optimal.

* **Time:** `O(R * C log(R * C))`

* **Space:** `O(R * C)`

---

### **Approach 3: Binary Search on Value (Optimal ✅)**

Since each row is sorted, we can apply **binary search on the value range**:

1. Find `min` (first element of rows) and `max` (last element of rows).
2. Binary search between `[min, max]`.
3. For each `mid`, count how many elements `<= mid`.

   * Use `upper_bound` (binary search) on each row.
4. If count ≤ `(n*m)/2`, shift right; else shift left.

* **Time:** `O( log(max-min) * R * logC )`
* **Space:** `O(1)`

---

## 🔹 Java Code (Optimal Approach)

```java
import java.util.*;

public class MatrixMedian {

    // Upper bound function
    static int upperBound(int[] row, int target) {
        int low = 0, high = row.length;
        while (low < high) {
            int mid = (low + high) / 2;
            if (row[mid] <= target) {
                low = mid + 1;
            } else {
                high = mid;
            }
        }
        return low; // count of elements <= target
    }

    public static int findMedian(int[][] matrix) {
        int R = matrix.length;
        int C = matrix[0].length;

        int min = Integer.MAX_VALUE;
        int max = Integer.MIN_VALUE;

        // Find global min and max
        for (int i = 0; i < R; i++) {
            min = Math.min(min, matrix[i][0]);
            max = Math.max(max, matrix[i][C - 1]);
        }

        int desired = (R * C + 1) / 2;

        while (min < max) {
            int mid = (min + max) / 2;
            int count = 0;

            for (int i = 0; i < R; i++) {
                count += upperBound(matrix[i], mid);
            }

            if (count < desired) {
                min = mid + 1;
            } else {
                max = mid;
            }
        }

        return min;
    }

    public static void main(String[] args) {
        int[][] matrix = {
            {1, 3, 5},
            {2, 6, 9},
            {3, 6, 9}
        };

        System.out.println("Median is: " + findMedian(matrix));
    }
}
```

---

✅ **Output**

```
Median is: 5
```

---

Do you want me to also give you the **Python version** (since binary search handling is a bit cleaner there) along with a **dry run** for better clarity?
