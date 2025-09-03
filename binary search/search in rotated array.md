
# 🔍 Search in Rotated Sorted Array (C++)

This program searches for a target element in a rotated sorted array using **binary search**.

A **rotated sorted array** is an array that was originally sorted in increasing order, but then rotated at some pivot. Example:
```

Original: \[0, 1, 2, 3, 4, 5, 6, 7]
Rotated:  \[3, 4, 5, 6, 7, 0, 1, 2]

````

---

## 📘 Explanation

We use a **modified binary search** to determine whether the **left or right half is sorted**, and then decide where the target might be.

Steps:
1. Check if the `mid` element is equal to the `target`.
2. If the **left half is sorted** (`nums[start] <= nums[mid]`):
   - Check if target lies in left range.
3. Else the **right half is sorted**:
   - Check if target lies in right range.
4. Repeat until found or array is exhausted.

---

## ✅ Code

```java
public class SearchInRotatedSortedArray {
    public static int search(int[] nums, int target) {
        int start = 0, end = nums.length - 1;

        while (start <= end) {
            int mid = start + (end - start) / 2;

            if (nums[mid] == target) {
                return mid;
            }

            // Left half is sorted
            if (nums[start] <= nums[mid]) {
                if (nums[start] <= target && target <= nums[mid]) {
                    end = mid - 1;
                } else {
                    start = mid + 1;
                }
            }
            // Right half is sorted
            else {
                if (nums[mid] <= target && target <= nums[end]) {
                    start = mid + 1;
                } else {
                    end = mid - 1;
                }
            }
        }

        return -1; // Target not found
    }

    public static void main(String[] args) {
        int[] nums = {3, 4, 5, 6, 7, 0, 1, 2};
        int target = 2;
        System.out.println(search(nums, target)); // Output: 7
    }
}

````

---

## 🧪 Input and Output

### 📝 Input:

```cpp
nums = [3, 4, 5, 6, 7, 0, 1, 2]
target = 2
```

### 📤 Output:

```
7
```

(2 is found at index `7`)

---

## ⏱ Time and Space Complexity

* **Time Complexity:** `O(log n)`
* **Space Complexity:** `O(1)`

---
