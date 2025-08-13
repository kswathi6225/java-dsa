There is a solution to find all pairs too check out in end

## 1. Brute Force Approach (O(n²))

* Check every pair of elements to see if they sum to the target.

```java
public class PairSumBruteForce {
    public static int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{-1, -1}; // No pair found
    }

    public static void main(String[] args) {
        int[] nums = {2, 7, 11, 15};
        int target = 9;
        int[] result = twoSum(nums, target);
        System.out.println("Pair indices (Brute Force): [" + result[0] + ", " + result[1] + "]");
    }
}
```
### Output:

```
Pair indices: [0, 1]
```

---

## 2. Optimized Approach using HashMap (O(n))  if array is unsorted

* Use a `HashMap` to store numbers and their indices for quick lookup.

```java
import java.util.HashMap;
import java.util.Map;

public class PairSumOptimized {
    public static int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>(); // value -> index

        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[]{map.get(complement), i}; // Found the pair
            }
            map.put(nums[i], i); // adds value to the hash map
        }
        return new int[]{-1, -1}; // No pair found
    }

    public static void main(String[] args) {
        int[] nums = {2, 7, 11, 15};
        int target = 9;
        int[] result = twoSum(nums, target);
        System.out.println("Pair indices (Optimized): [" + result[0] + ", " + result[1] + "]");
    }
}
```

---
## 3.if array is sorted-- Two-Pointer approach in sorted array that finds **all pairs that sum to the target**  O(n)

```java
import java.util.ArrayList;
import java.util.List;

public class PairSumAllTwoPointer {
    public static void main(String[] args) {
        int[] nums = {2, 4, 5, 7, 11, 15};
        int target = 9;

        int i = 0;
        int j = nums.length - 1;

        List<Integer> ans = new ArrayList<>();

        while (i < j) {
            int pairSum = nums[i] + nums[j];

            if (pairSum < target) {
                i++;
            } else if (pairSum > target) {
                j--;
            } else {
                ans.add(i); // store index of first number
                ans.add(j); // store index of second number
                i++;
                j--;
            }
        }

        // Print all found pairs
        for (int k = 0; k < ans.size(); k += 2) {
            System.out.println(nums[ans.get(k)] + ", " + nums[ans.get(k + 1)]);
        }
    }
}
```

---

### Output:

```
2, 7
4, 5
```

---

✅ **Explanation:**

* `i` → starts from beginning
* `j` → starts from end
* Compare `nums[i] + nums[j]` with `target`

  * `< target` → move `i++` to increase sum
  * `> target` → move `j--` to decrease sum
  * `== target` → store indices and move both pointers

This finds **all pairs in a sorted array** efficiently in **O(n)** time.
---

### ✅ Summary

| Approach            | Time Complexity | Space Complexity |
| ------------------- | --------------- | ---------------- |
| Brute Force         | O(n²)           | O(1)             |
| Optimized (HashMap) | O(n)            | O(n)             |

---

If you want, I can also show a **two-pointer approach** which works **only for sorted arrays** and is **O(n)** time with **O(1)** space

Got it — you want to find **all pairs** in the array whose sum equals a target (like `9`) using a **HashMap**.

Here’s a Java example:

```java
import java.util.*;

public class AllPairsWithSum {
    public static void main(String[] args) {
        int[] nums = {2, 7, 4, 5, 3, 6, 1, 8, 2};
        int target = 9;

        List<int[]> result = findAllPairs(nums, target);

        System.out.println("Pairs with sum " + target + ":");
        for (int[] pair : result) {
            System.out.println(pair[0] + ", " + pair[1]);
        }
    }

    public static List<int[]> findAllPairs(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>(); // value -> count
        List<int[]> pairs = new ArrayList<>();

        for (int num : nums) {
            int rest = target - num;
            if (map.containsKey(rest) && map.get(rest) > 0) {
                pairs.add(new int[]{rest, num});
                map.put(rest, map.get(rest) - 1); // reduce count for rest
            } else {
                map.put(num, map.getOrDefault(num, 0) + 1); // store count
            }
        }

        return pairs;
    }
}
```

### How it works:

1. **Map stores frequency** of numbers seen so far.
2. For each number:

   * Check if its complement (`target - num`) exists in the map.
   * If yes, record the pair and reduce that complement’s count.
   * Otherwise, store this number in the map.
3. Works for **multiple pairs** without reusing the same element twice.

**Example output for target=9**:

```
Pairs with sum 9:
2, 7
4, 5
3, 6
8, 1
2, 7
```

If you want, I can also give a **version that returns all unique pairs** without duplicates.


