
### 🔹 Case 1: Convert `[1,2,3,4,5]` → `[2,1,4,3,5]` (→ `21435`)

👉 This looks like **pairwise swapping**: swap `(1,2)` and `(3,4)`.

#### Code:

```java
import java.util.*;

public class RearrangePairs {
    public static void main(String[] args) {
        int[] arr2 = {1,2,3,4,5};
        
        // Swap in pairs
        for(int i=0; i < arr2.length-1; i+=2){
            int temp = arr2[i];
            arr2[i] = arr2[i+1];
            arr2[i+1] = temp;
        }
        
        System.out.println("21435 -> " + Arrays.toString(arr2));
    }
}
```

✅ Output:

```
21435 -> [2, 1, 4, 3, 5]
```

---

### ⏱ Time Complexities
* **Pairwise Swap (21435):**

  * One pass → `O(n)`
  * Space → `O(1)`

---
Got it 👍
You want to **swap every element with the element that is 2 places ahead in the array** (i.e., swap index `i` with index `i+2` if possible).

Let’s do this step by step in **Java** 👇

---

### Approach 1: Simple Iteration (swap with i+2)

```java
public class SwapByTwo {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};

        // Swap every element with element 2 places ahead
        for (int i = 0; i < arr.length - 2; i++) {
            int temp = arr[i];
            arr[i] = arr[i + 2];
            arr[i + 2] = temp;
        }

        // Print result
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

---

### 🔹 Example Dry Run

Input: `1 2 3 4 5`

* Swap index `0` & `2` → `3 2 1 4 5`
* Swap index `1` & `3` → `3 4 1 2 5`
* Index `2` & `4` → `3 4 5 2 1`

Output:

```
3 4 5 2 1
```

---

### Approach 2: Only Swap Disjoint Pairs

If you mean only swap `(0,2)`, `(2,4)`, … (not overlapping swaps):

```java
public class SwapByTwoDisjoint {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};

        // Swap disjoint pairs
        for (int i = 0; i < arr.length - 2; i += 2) {
            int temp = arr[i];
            arr[i] = arr[i + 2];
            arr[i + 2] = temp;
        }

        // Print result
        for (int num : arr) {
            System.out.print(num + " ");
        }
    }
}
```

---

### 🔹 Example Dry Run

Input: `1 2 3 4 5`

* Swap index `0` & `2` → `3 2 1 4 5`
* Swap index `2` & `4` → `3 2 5 4 1`

Output:

```
3 2 5 4 1
```

---

✅ **Time Complexity:** O(n)
✅ **Space Complexity:** O(1) (in-place swapping)

---

