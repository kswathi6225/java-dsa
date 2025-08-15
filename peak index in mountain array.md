### 🏔️ What is a Mountain Array?

A **mountain array** is defined as:

* An array where:

  * Elements strictly **increase to a peak**, and then
  * Strictly **decrease** after the peak.
* It has **at least 3 elements**, like:

  ```cpp
  [1, 3, 5, 6, 4, 2]
              ↑
           (peak)
  ```

---
### 🏔️ **Java Code – Find Peak Index in a Mountain Array**

```java
public class MountainArrayPeak {
    public static int peakIndex(int[] arr) {
        int start = 0, end = arr.length - 1;

        while (start < end) { // ensures mid+1 is always valid
            int mid = start + (end - start) / 2;

            if (arr[mid] < arr[mid + 1]) {
                // Increasing part → move right
                start = mid + 1;
            } else {
                // Decreasing part → peak is at mid or to the left
                end = mid;
            }
        }
        // start == end → peak index
        return start;
    }

    public static void main(String[] args) {
        int[] arr = {0, 3, 8, 9, 5, 2};
        System.out.println("Peak index: " + peakIndex(arr));
    }
}
```

---

### ✅ Output

```
Peak index: 3
```

---

### ⏱️ **Time & Space Complexity**

* **Time:** `O(log n)` – Binary Search
* **Space:** `O(1)` – Constant extra space

---

If you want, I can also give you a **Java version that directly returns the peak value** instead of the index, depending on what your problem statement requires.
