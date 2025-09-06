Sure! This is **LeetCode 414 – Third Maximum Number**.
We need to find the **third distinct maximum number**, and if it doesn’t exist, return the **maximum number**.

Here’s an **optimal Java solution** using a **single pass** and **O(1) space** (no extra sorting or sets needed):

---

### ✅ Java Code

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] nums = {3, 2, 1};
        System.out.println(thirdMax(nums));
    }

    public static int thirdMax(int[] nums) {
        Long max1 = null, max2 = null, max3 = null;

        for (Integer num : nums) {
            if (num.equals(max1) || num.equals(max2) || num.equals(max3)) continue; // skip duplicates

            if (max1 == null || num > max1) {
                max3 = max2;
                max2 = max1;
                max1 = (long) num;
            } else if (max2 == null || num > max2) {
                max3 = max2;
                max2 = (long) num;
            } else if (max3 == null || num > max3) {
                max3 = (long) num;
            }
        }

        return max3 != null ? max3.intValue() : max1.intValue();
    }
}
```

---

### ✅ How It Works

1. Keep track of **top three distinct maximums** (`max1 > max2 > max3`).
2. Skip **duplicate numbers**.
3. If the **third maximum exists**, return it.
4. Otherwise, return the **maximum number** (`max1`).

---

### ✅ Example Runs

**Example 1**
Input: `[3,2,1]` → Output: `1`

**Example 2**
Input: `[1,2]` → Output: `2` (third maximum doesn’t exist, return max)

**Example 3**
Input: `[2,2,3,1]` → Output: `1` (distinct maximums: 3,2,1)

---

### ✅ Complexity

* **Time:** `O(n)` → single pass
* **Space:** `O(1)` → constant extra space

---

If you want, I can also show the **alternative solution using a TreeSet** which is shorter but uses `O(n)` extra space.

Do you want me to show that version too?
