Sure! Let’s go **step by step** for **moving all zeroes to the end of an array** while maintaining the order of non-zero elements.

---

# **Problem:**

Given an array `nums`, **move all 0’s to the end** **in-place** while keeping the relative order of non-zero elements.

**Example:**

```
Input:  [0, 1, 0, 3, 12]
Output: [1, 3, 12, 0, 0]
```

---

# **Optimal Approach (Two Pointers / In-place)**

### **Idea:**

1. Use a pointer `j` to keep track of the **next position to place a non-zero element**.
2. Iterate through the array:

   * If the element is non-zero, place it at `nums[j]` and increment `j`.
3. After the loop, **fill remaining positions with 0**.

---

### ✅ Java Code

```java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] nums = {0, 1, 0, 3, 12};
        moveZeroes(nums);
        System.out.println(Arrays.toString(nums));
    }

    public static void moveZeroes(int[] nums) {
        int j = 0; // position to place next non-zero

        // Step 1: Move all non-zero elements to the front
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[j] = nums[i];
                j++;
            }
        }

        // Step 2: Fill remaining positions with zero
        while (j < nums.length) {
            nums[j] = 0;
            j++;
        }
    }
}
```

---

### ✅ Input / Output

**Input:**

```
[0, 1, 0, 3, 12]
```

**Output:**

```
[1, 3, 12, 0, 0]
```

---

### ✅ Complexity

| Operation | Complexity      |
| --------- | --------------- |
| Time      | O(n)            |
| Space     | O(1) (in-place) |

---

This is **the optimal approach**, much better than swapping each zero individually.

I can also show a **slightly shorter version that swaps zero and non-zero directly** in one pass, which is sometimes faster in practice.

Do you want me to show that version?
