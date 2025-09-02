Great one 👍 Let’s go through **Search Insert Position** step by step — it’s a very common LeetCode problem (`#35`).

---

# 🔹 Problem: Search Insert Position

You are given a sorted array of distinct integers and a target value.
Return the **index** if the target is found.
If not, return the **index where it would be inserted** in order.

---

## ✅ Example

```
Input: nums = [1,3,5,6], target = 5
Output: 2   (found at index 2)

Input: nums = [1,3,5,6], target = 2
Output: 1   (insert at index 1)

Input: nums = [1,3,5,6], target = 7
Output: 4   (insert at end)

Input: nums = [1,3,5,6], target = 0
Output: 0   (insert at beginning)
```

---

# 🔹 Approaches

## 1️⃣ Linear Search (Brute Force)

* Traverse array, return first index where `nums[i] >= target`.
* If no such index, insert at end.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)`

```java
public class SearchInsertPosition {
    public static int searchInsert(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] >= target) {
                return i;
            }
        }
        return nums.length; // insert at end
    }

    public static void main(String[] args) {
        int[] nums = {1,3,5,6};
        int target = 2;
        System.out.println(searchInsert(nums, target)); // Output: 1
    }
}
```

---

## 2️⃣ Binary Search (Optimized)

Since the array is sorted, we can use **Binary Search**.

**Time Complexity:** `O(log n)`
**Space Complexity:** `O(1)`

```java
public class SearchInsertPosition {
    public static int searchInsert(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        
        while (left <= right) {
            int mid = left + (right - left) / 2;
            
            if (nums[mid] == target) {
                return mid; // found
            } else if (nums[mid] < target) {
                left = mid + 1; // move right
            } else {
                right = mid - 1; // move left
            }
        }
        // left will be at the correct insert position
        return left;
    }

    public static void main(String[] args) {
        int[] nums = {1,3,5,6};
        int target = 7;
        System.out.println(searchInsert(nums, target)); // Output: 4
    }
}
```

---

# 🔹 Key Idea

👉 After binary search ends,

* If target not found,
* `left` will be the correct **insert position**.

---

Would you like me to next explain **"Find First and Last Position of Element in Sorted Array"** (very related to this problem), or continue to another different type of array/binary search problem?
