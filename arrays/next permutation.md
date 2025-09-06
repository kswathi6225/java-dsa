# **Next Permutation**

**Problem:**
Given an array of numbers, rearrange them to the **next lexicographical permutation**.
If the current permutation is the **largest**, rearrange it to the **smallest (sorted ascending)**.

**Example:**

```
Input:  nums = [1, 2, 3]
Output: [1, 3, 2]

Input: nums = [3, 2, 1]
Output: [1, 2, 3]
```

---

# **Algorithm (Steps)**

1. Start from the **end of the array** and find the **first index `i`** such that `nums[i] < nums[i+1]`.

   * This is the number that needs to be increased to get the next permutation.

2. If no such `i` exists, the array is in descending order → **reverse it** to get the smallest permutation.

3. Otherwise, find the **smallest number greater than `nums[i]`** to the right of `i`, call it `nums[j]`.

4. **Swap `nums[i]` and `nums[j]`**.

5. **Reverse the subarray from `i+1` to end** to get the next permutation in lexicographic order.

---

### ✅ Java Code

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] nums = {1, 2, 3};
        nextPermutation(nums);
        System.out.println(Arrays.toString(nums));
    }

    public static void nextPermutation(int[] nums) {
        int n = nums.length;
        int i = n - 2;

        // Step 1: Find the first decreasing element from the end
        while (i >= 0 && nums[i] >= nums[i + 1]) i--;

        if (i >= 0) {
            // Step 2: Find the element just larger than nums[i]
            int j = n - 1;
            while (nums[j] <= nums[i]) j--;
            swap(nums, i, j);
        }

        // Step 3: Reverse the subarray from i+1 to end
        reverse(nums, i + 1, n - 1);
    }

    static void swap(int[] nums, int i, int j) {
        int t = nums[i]; nums[i] = nums[j]; nums[j] = t;
    }

    static void reverse(int[] nums, int start, int end) {
        while (start < end) swap(nums, start++, end--);
    }
}
```

---

### ✅ Example Runs

**Input:** `[1, 2, 3]` → Output: `[1, 3, 2]`
**Input:** `[1, 3, 2]` → Output: `[2, 1, 3]`
**Input:** `[3, 2, 1]` → Output: `[1, 2, 3]`

---

### ✅ Complexity

| Operation | Complexity |
| --------- | ---------- |
| Time      | O(n)       |
| Space     | O(1)       |
| In-place  | Yes        |

---

If you want, I can also **show a step-by-step dry run for `[1, 2, 3]` → `[1, 3, 2]`** so it becomes super clear why it works.

Do you want me to do that?
