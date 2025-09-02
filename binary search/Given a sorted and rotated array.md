Great question 👍 This is a very common binary search interview problem.
We are asked: **Given a sorted and rotated array, find the number of times the array has been rotated.**

---

## 🔹 Key Idea

* In a **sorted rotated array**, the **index of the minimum element** is the number of times the array has been rotated.
* Example:

  ```
  arr = [15, 18, 2, 3, 6, 12]
  Sorted array before rotation = [2, 3, 6, 12, 15, 18]
  Minimum element = 2 → index = 2  
  So, array rotated 2 times.
  ```

---

## 🔹 Approaches

### 1. **Linear Search (Naive)**

* Traverse the array, find the index of the smallest element.
* That index = number of rotations.

⏱ Time: `O(n)`
📦 Space: `O(1)`

```java
public class RotationCount {
    public static int rotationCountLinear(int[] arr) {
        int n = arr.length;
        int minIndex = 0;

        for (int i = 1; i < n; i++) {
            if (arr[i] < arr[minIndex]) {
                minIndex = i;
            }
        }
        return minIndex;
    }

    public static void main(String[] args) {
        int arr[] = {15, 18, 2, 3, 6, 12};
        System.out.println("Array rotated " + rotationCountLinear(arr) + " times");
    }
}
```

---

### 2. **Binary Search (Optimized)**

* Use **modified binary search**:

  * If `arr[mid] <= arr[high]`, then minimum lies in the left half.
  * Else, minimum lies in the right half.
* When found, return its index.

⏱ Time: `O(log n)`
📦 Space: `O(1)`

```java
public class RotationCount {
    public static int rotationCountBinary(int[] arr) {
        int n = arr.length;
        int low = 0, high = n - 1;

        while (low <= high) {
            // If already sorted
            if (arr[low] <= arr[high]) {
                return low;
            }

            int mid = low + (high - low) / 2;
            int next = (mid + 1) % n;
            int prev = (mid - 1 + n) % n;

            // Check if mid is minimum
            if (arr[mid] <= arr[next] && arr[mid] <= arr[prev]) {
                return mid;
            }

            // Decide which side to go
            if (arr[mid] <= arr[high]) {
                high = mid - 1; // go left
            } else {
                low = mid + 1; // go right
            }
        }
        return -1;
    }

    public static void main(String[] args) {
        int arr[] = {15, 18, 2, 3, 6, 12};
        System.out.println("Array rotated " + rotationCountBinary(arr) + " times");
    }
}
```

---

✅ Example Output:

```
Array rotated 2 times
```

---

Do you want me to also cover the **case with duplicates** (like `[2, 2, 2, 3, 4, 2]`) where standard binary search can fail?
