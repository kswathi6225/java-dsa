### **Problem Definition**

A **majority element** in an array is the element that appears **more than ⌊n/2⌋ times** (where `n` is the size of the array).

Example:

```java
Input: nums = [3, 3, 4, 2, 3, 3, 5]
Output: 3
```

Because `3` appears 4 times in a length 7 array (`4 > 7/2`).

---

## **Approach 1 – Brute Force (O(n²) time, O(1) space)**

We check each element’s frequency by looping through the array.

```java
public class MajorityElementBrute {
    public static void main(String[] args) {
        int[] nums = {3, 3, 4, 2, 3, 3, 5};
        int n = nums.length;
        int majority = -1;

        for (int i = 0; i < n; i++) {
            int count = 0;
            for (int j = 0; j < n; j++) {
                if (nums[j] == nums[i]) {
                    count++;
                }
            }
            if (count > n / 2) {
                majority = nums[i];
                break;
            }
        }

        System.out.println("Majority Element: " + majority);
    }
}
```

**Time Complexity:** O(n²)
**Space Complexity:** O(1)

---

## **Approach 2 – Using HashMap (O(n) time, O(n) space)**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] nums = {3, 3, 4, 2, 3, 3, 5};
        Map<Integer, Integer> map = new HashMap<>();
        int n = nums.length;

        // Count frequency of each number
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        int majority = -1;

        // Check if any number appears more than n/2 times
        for (int num : map.keySet()) {
            if (map.get(num) > n / 2) {
                majority = num;
                break;
            }
        }

        System.out.println("Majority Element: " + majority);
    }
}

```

**Time Complexity:** O(n)
**Space Complexity:** O(n)

---
## [Better Approach - 1] Using Sorting - O(nlog(n)) Time and O(1) Space

```java
import java.util.Arrays;

class GfG {

    static int majorityElement(int[] arr) {

        int n = arr.length;
        Arrays.sort(arr);
        
        // Potential majority element
        int candidate = arr[n/2];  
        
        // Count how many times candidate appears
        int count = 0;
        for (int num : arr) {
            if (num == candidate) {
                count++;
            }
        }
    
        if (count > n/2) {
            return candidate;
        }
        // No majority element
        return -1;  
    }

    public static void main(String[] args) {
        int[] arr = {1, 1, 2, 1, 3, 5, 1};
        System.out.println(majorityElement(arr));
    }
}
```
## **Approach 3 – Boyer-Moore Voting Algorithm (O(n) time, O(1) space)** ✅ **Most Optimal**

This is the best way to solve it when the majority element is guaranteed to exist.

```java
public class MajorityElementOptimal {
    public static void main(String[] args) {
        int[] nums = {3, 3, 4, 2, 3, 3, 5};
        int count = 0;
        int candidate = 0;

        // Phase 1: Find a candidate
        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }
            count += (num == candidate) ? 1 : -1;
        }

        // Phase 2: Verify the candidate
        count = 0;
        for (int num : nums) {
            if (num == candidate) count++;
        }

        if (count > nums.length / 2) {
            System.out.println("Majority Element: " + candidate);
        } else {
            System.out.println("No Majority Element");
        }
    }
}
```

**Time Complexity:** O(n)
**Space Complexity:** O(1)

---

If you want, we can now move to **finding all elements that appear more than ⌊n/3⌋ times** — that’s like the “advanced” version of this problem.
It’s a twist on Boyer-Moore.

Do you want me to show that next?
