Here’s a **small, brief explanation of Monotonic Stack** in markdown with code:

---

# 📌 Monotonic Stack (Brief)

A **monotonic stack** is a stack that keeps elements either in **increasing order** or **decreasing order**.
It is widely used in problems like **Next Greater Element**, **Stock Span**, **Trapping Rain Water**, etc.

---

## ✅ Types

1. **Monotonic Increasing Stack**

   * Elements in the stack are **always increasing**.
   * Pop elements when you encounter a **smaller** one.
   * Useful for **next smaller element problems**.

2. **Monotonic Decreasing Stack**

   * Elements in the stack are **always decreasing**.
   * Pop elements when you encounter a **greater** one.
   * Useful for **next greater element problems**.

---

## 🔹 Example: Next Greater Element (Monotonic Decreasing Stack)

```java
import java.util.*;

public class NextGreaterElement {
    public static int[] nextGreater(int[] nums) {
        int n = nums.length;
        int[] result = new int[n];
        Arrays.fill(result, -1);

        Stack<Integer> stack = new Stack<>(); // store indices

        for (int i = 0; i < n; i++) {
            // Pop while current num is greater than stack's top element
            while (!stack.isEmpty() && nums[i] > nums[stack.peek()]) {
                int idx = stack.pop();
                result[idx] = nums[i];
            }
            stack.push(i);
        }
        return result;
    }

    public static void main(String[] args) {
        int[] nums = {2, 1, 5, 3, 7};
        System.out.println(Arrays.toString(nextGreater(nums)));
        // Output: [5, 5, 7, 7, -1]
    }
}
```

---

## ⏱️ Time & Space Complexity

* **Time**: `O(n)` → Each element is pushed & popped at most once.
* **Space**: `O(n)` for stack & result array.

---

👉 In interviews, explain monotonic stack as:
*"A stack-based technique where elements are stored in sorted order (increasing/decreasing). It helps in solving range queries like next greater/smaller element efficiently in linear time."*

---

Do you want me to also make a **diagram step-by-step dry run** of the above example so you can explain visually in interviews?
