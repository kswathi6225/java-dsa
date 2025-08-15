## **1. Linear Search**

* **Works on:** Any type of array (sorted or unsorted)
* **Logic:** Check each element one by one until the target is found or the list ends
* **Time Complexity:** O(n)

```java
public class LinearSearchExample {
    public static int linearSearch(int[] arr, int target) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == target) {
                return i; // Found → return index
            }
        }
        return -1; // Not found
    }

    public static void main(String[] args) {
        int[] arr = {5, 8, 2, 9, 1};
        int target = 9;
        int result = linearSearch(arr, target);

        if (result != -1)
            System.out.println("Element found at index: " + result);
        else
            System.out.println("Element not found");
    }
}
```

---

## **2. Binary Search**

* **Works on:** **Sorted** arrays only
* **Logic:** Repeatedly divide the search range into half until the element is found
* **Time Complexity:** O(log n)

### **Iterative Version**

```java
import java.util.Arrays;

public class BinarySearchExample {
    public static int binarySearch(int[] arr, int target) {
        int left = 0, right = arr.length - 1;
        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (arr[mid] == target)
                return mid; // Found → return index
            if (arr[mid] < target)
                left = mid + 1; // Search right half
            else
                right = mid - 1; // Search left half
        }
        return -1; // Not found
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 5, 8, 9};
        int target = 8;
        int result = binarySearch(arr, target);

        if (result != -1)
            System.out.println("Element found at index: " + result);
        else
            System.out.println("Element not found");
    }
}
```
## ✅ Method 2: Binary Search (Optimized Mid Calculation)

### 🔹 Description:
This method is similar to **Method 1**, but it uses a more optimized and **safe way** to calculate the mid-point:
```cpp
mid = start + (end - start) / 2;
````

### 🧠 Time Complexity: `O(log n)`

### 🧠 Space Complexity: `O(1)` (Iterative – constant space)

---

### 🚀 Why this is better than `(start + end) / 2`?

If `start` and `end` are **very large integers**, then adding them may cause **integer overflow**.

✅ Safer Formula:

```cpp
mid = start + (end - start) / 2;
```

✅ This prevents overflow by computing the **distance** between `start` and `end`, then adding it to `start`.

---

### ✅ When to Use This Optimized Version:

* When working with **very large input arrays** (like `10^9` elements).
* In **competitive programming** or **system-level code** where overflow must be avoided.
* When solving problems on **platforms like LeetCode, Codeforces, HackerRank**, etc.

---

### 🧠 Bonus Tip:

This optimized mid is often used by **default in interviews** and is considered **best practice** in all production-level code.


---

✅ **Key Difference:**

| Feature                | Linear Search | Binary Search    |
| ---------------------- | ------------- | ---------------- |
| Works on sorted array? | No            | Yes              |
| Time Complexity        | O(n)          | O(log n)         |
| Approach               | Sequential    | Divide & Conquer |

---

If you want, I can give you a **Java program that takes input from the user** and demonstrates **both searches side-by-side** so you can compare them in one run. That way, you can test with different arrays and see the difference.
