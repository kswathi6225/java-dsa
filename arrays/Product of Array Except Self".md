**"Product of Array Except Self"** 
Given an array `nums`, return an array `output` where `output[i]` is the product of all elements except `nums[i]`.
Example:

```
Input:  nums = [1, 2, 3, 4]
Output: [24, 12, 8, 6]
```

---

## **Approach 1: Brute Force (O(n²) time, O(1) extra space)**

* For each element, multiply all other elements.
* **Not efficient** for large arrays.

```java
public class ProductExceptSelf {
    public static int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];

        for (int i = 0; i < n; i++) {
            int product = 1;
            for (int j = 0; j < n; j++) {
                if (i != j) {
                    product *= nums[j];
                }
            }
            result[i] = product;
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4};
        int[] res = productExceptSelf(nums);
        for (int val : res) {
            System.out.print(val + " ");
        }
    }
}
```

---

## **Approach 2: Prefix & Suffix Arrays (O(n) time, O(n) extra space)**

* Compute prefix products and suffix products separately.
* Multiply prefix\[i] and suffix\[i] to get the result.

```java
public class ProductExceptSelf {
    public static int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] prefix = new int[n];
        int[] suffix = new int[n];
        int[] result = new int[n];

        // Prefix product
        prefix[0] = 1;
        for (int i = 1; i < n; i++) {
            prefix[i] = prefix[i - 1] * nums[i - 1];
        }

        // Suffix product
        suffix[n - 1] = 1;
        for (int i = n - 2; i >= 0; i--) {
            suffix[i] = suffix[i + 1] * nums[i + 1];
        }

        // Final result
        for (int i = 0; i < n; i++) {
            result[i] = prefix[i] * suffix[i];
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4};
        int[] res = productExceptSelf(nums);
        for (int val : res) {
            System.out.print(val + " ");
        }
    }
}
```

---

## **Approach 3: Optimized Space (O(n) time, O(1) extra space)**

* Store result as prefix product first.
* Multiply with running suffix product in second pass.

```java
public class ProductExceptSelf {
    public static int[] productExceptSelf(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];

        // First pass: prefix products
        result[0] = 1;
        for (int i = 1; i < n; i++) {
            result[i] = result[i - 1] * nums[i - 1];
        }

        // Second pass: multiply with suffix products
        int suffix = 1;
        for (int i = n - 1; i >= 0; i--) {
            result[i] *= suffix;
            suffix *= nums[i];
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4};
        int[] res = productExceptSelf(nums);
        for (int val : res) {
            System.out.print(val + " ");
        }
    }
}
```

✅ **Best Choice:** Approach 3 → **O(n)** time and **O(1)** extra space (excluding output array).

---

If you want, I can also **add a handling for zero values** in the array since that changes the logic slightly.
Do you want me to include that version too?
