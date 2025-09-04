Got it 👍 This is a follow-up of **Search in Rotated Sorted Array**, but with **duplicates allowed**.
The key difference:
👉 When duplicates are present, the condition `arr[left] <= arr[mid]` or `arr[mid] <= arr[right]` may fail because `arr[left] == arr[mid] == arr[right]`.
👉 To handle this, we just **shrink the search space** by doing `left++` and `right--` in that case.

---

## ✅ Java Code: Search in Rotated Sorted Array II

```java
public class SearchRotatedArrayII {
    public static boolean search(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) {
                return true; // found
            }

            // Handle duplicates
            if (nums[left] == nums[mid] && nums[mid] == nums[right]) {
                left++;
                right--;
            }
            // Left half is sorted
            else if (nums[left] <= nums[mid]) {
                if (nums[left] <= target && target < nums[mid]) {
                    right = mid - 1; // search in left half
                } else {
                    left = mid + 1; // search in right half
                }
            }
            // Right half is sorted
            else {
                if (nums[mid] < target && target <= nums[right]) {
                    left = mid + 1; // search in right half
                } else {
                    right = mid - 1; // search in left half
                }
            }
        }
        return false; // not found
    }

    public static void main(String[] args) {
        int[] arr = {2, 5, 6, 0, 0, 1, 2};
        int target = 0;
        System.out.println(search(arr, target)); // true

        target = 3;
        System.out.println(search(arr, target)); // false
    }
}
```

---

## ✅ Complexity

* **Time Complexity:**

  * Worst case: `O(N)` (when duplicates force us to shrink one-by-one).
  * Average case: `O(log N)` (like normal binary search).
* **Space Complexity:** `O(1)`

---

Would you like me to **dry run with the input** `arr = [2, 5, 6, 0, 0, 1, 2], target = 0` so you can see how duplicates affect the search?
