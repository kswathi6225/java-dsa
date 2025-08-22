Great question 👍
"Next Greater Element" (NGE) is a **classic stack problem** often asked in interviews.

---

### Problem:

For each element in an array, find the **next greater element** to its right.
If no greater element exists, return **-1** for that position.

---

### Example:

```
Input:  [4, 5, 2, 25]
Output: [5, 25, 25, -1]

Explanation:  
4 → next greater is 5  
5 → next greater is 25  
2 → next greater is 25  
25 → no greater → -1
```
----
## Brute Force Code (O(n²)):
```java
import java.util.*;

public class NextGreaterElement {
    public static void main(String[] args) {
        int arr[] = {4, 5, 2, 25};
        int n = arr.length;

        // Result array
        int[] nge = new int[n];

        // For each element, check to the right
        for (int i = 0; i < n; i++) {
            nge[i] = -1; // default if no greater element
            for (int j = i + 1; j < n; j++) {
                if (arr[j] > arr[i]) {
                    nge[i] = arr[j];
                    break; // stop once we find the first greater element
                }
            }
        }

        // Print the result
        System.out.println("Element -> Next Greater Element");
        for (int i = 0; i < n; i++) {
            System.out.println(arr[i] + " -> " + nge[i]);
        }
    }
}
```
---

### Approach (Using Stack - O(n)):

* Traverse the array **from right to left**.
* Use a stack to keep track of "candidates" for next greater.
* For each element:

  * Pop from stack until you find a greater element.
  * If stack is empty → answer is -1.
  * Else top of stack is the next greater.
  * Push the current element into stack.

---

### Java Code:

```java
import java.util.*;

public class NextGreaterElement {
    public static void main(String[] args) {
        int arr[] = {4, 5, 2, 25};
        int n = arr.length;
        int result[] = new int[n];

        Stack<Integer> stack = new Stack<>();

        // Traverse from right to left
        for (int i = n - 1; i >= 0; i--) {
            // Pop smaller or equal elements
            while (!stack.isEmpty() && stack.peek() <= arr[i]) {
                stack.pop();
            }

            // If stack is empty, no greater element
            if (stack.isEmpty()) {
                result[i] = -1;
            } else {
                result[i] = stack.peek();
            }

            // Push current element
            stack.push(arr[i]);
        }

        // Print result
        System.out.println("Next Greater Elements:");
        for (int i = 0; i < n; i++) {
            System.out.println(arr[i] + " -> " + result[i]);
        }
    }
}
```

---

### Output:

```
Next Greater Elements:
4 -> 5
5 -> 25
2 -> 25
25 -> -1
```

---

👉 This is a **must-know stack problem** and is often extended to **circular arrays** or **next smaller element** versions in interviews.

Do you want me to also show you the **brute force O(n²) approach** for comparison (so you’ll see why stack is better)?
