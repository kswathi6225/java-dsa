## 🔹 **Lower Bound & Upper Bound**

* **Lower Bound** → the **first index** where element ≥ target.
* **Upper Bound** → the **first index** where element > target.

### Example:

Array = `[1, 2, 4, 4, 5, 7]`

* `lower_bound(4)` → index **2** (first `4`)
* `upper_bound(4)` → index **4** (first element greater than `4`, i.e. `5`)

---

## ✅ Code in Java

```java
public class Bounds {

    // Lower Bound: first index where arr[index] >= target
    public static int lowerBound(int[] arr, int target) {
        int low = 0, high = arr.length;
        while (low < high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] < target) {
                low = mid + 1;   // go right
            } else {
                high = mid;      // possible answer, go left
            }
        }
        return low;  // index of lower bound
    }

    // Upper Bound: first index where arr[index] > target
    public static int upperBound(int[] arr, int target) {
        int low = 0, high = arr.length;
        while (low < high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] <= target) {
                low = mid + 1;   // go right
            } else {
                high = mid;      // possible answer, go left
            }
        }
        return low;  // index of upper bound
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 4, 4, 5, 7};

        int lb = lowerBound(arr, 4);
        int ub = upperBound(arr, 4);

        System.out.println("Lower Bound of 4 = " + lb); // 2
        System.out.println("Upper Bound of 4 = " + ub); // 4
    }
}
```

---

## ⏱ Complexity

* **Time:** `O(log n)` (binary search).
* **Space:** `O(1)` (only variables used).

---

👉 Do you want me to also show how to implement **C++ STL equivalents** (`std::lower_bound`, `std::upper_bound`) manually in C++ code, or just stick with Java?
