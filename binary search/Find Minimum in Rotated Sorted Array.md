# 🔹 Problem: Find Minimum in Rotated Sorted Array

You are given a rotated sorted array (ascending order, rotated at some pivot).
👉 Task: Find the **minimum element**.

### Example

```
Input: [4,5,6,7,0,1,2]
Output: 0
```

---

# 🔹 Approaches

### 1. **Brute Force**

* Simply traverse and find the minimum.
* **Time:** O(n)
* **Space:** O(1)

```java
class Solution {
    public int findMin(int[] nums) {
        int min = nums[0];
        for (int num : nums) {
            min = Math.min(min, num);
        }
        return min;
    }
}
```

---

### 2. **Optimized Binary Search** (✅ Most Important)

* Key idea:

  * If the array is not rotated → first element is min.
  * Use **binary search** to find the "inflection point".
  * If `nums[mid] > nums[high]` → min is in right half.
  * Else → min is in left half (including mid).

* **Time:** O(log n)

* **Space:** O(1)

```java
class Solution {
    public int findMin(int[] nums) {
        int low = 0, high = nums.length - 1;
        
        while (low < high) {
            int mid = low + (high - low) / 2;
            
            if (nums[mid] > nums[high]) {
                // Minimum lies in the right half
                low = mid + 1;
            } else {
                // Minimum lies in the left half (including mid)
                high = mid;
            }
        }
        return nums[low]; // low == high → min element
    }
}
```

---
GO DOWN THERE IS ONE MORE METHOD
### 3. **Recursive Binary Search** (less common but interviewers may ask)

```java
class Solution {
    public int findMin(int[] nums) {
        return searchMin(nums, 0, nums.length - 1);
    }
    
    private int searchMin(int[] nums, int low, int high) {
        if (low == high) return nums[low];
        
        int mid = low + (high - low) / 2;
        
        if (nums[mid] > nums[high]) {
            return searchMin(nums, mid + 1, high);
        } else {
            return searchMin(nums, low, mid);
        }
    }
}
```

---

### 🔹 With Duplicates

If duplicates exist, binary search can get stuck.
So:

* When `nums[mid] == nums[right]`, we **can’t decide**, so just do `right--`.

---

### 🔹 Java Code (With Duplicates)

```java
public class Main {
    public static int findMin(int[] nums) {
        int left = 0, right = nums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] > nums[right]) {
                left = mid + 1;
            } else if (nums[mid] < nums[right]) {
                right = mid;
            } else {
                // nums[mid] == nums[right], can't decide, shrink
                right--;
            }
        }
        return nums[left];
    }

    public static void main(String[] args) {
        int[] arr = {2,2,2,0,1};
        System.out.println(findMin(arr)); // 0
    }
}
```

⏱ **Time Complexity**: O(log n) on average, but **O(n) worst case** (all duplicates).

---

✅ **Best Approach:** Iterative Binary Search (O(log n), O(1))
✅ **Brute Force:** Use only for understanding.

---

Do you want me to also cover the **"Find Minimum in Rotated Sorted Array with Duplicates"** version (a common follow-up in interviews)?
