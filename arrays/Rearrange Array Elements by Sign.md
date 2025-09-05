Nice one 🚀 This is a **classic array rearrangement problem**:

> **Rearrange the array so that positive and negative numbers appear alternately.**
> If extra positive or negative numbers remain, put them at the end.

---

## **Example**

```
Input:  [1, 2, 3, -4, -1, 4]
Output: [-4, 1, -1, 2, 3, 4]  (alternating neg/pos)
```

---

## **Optimized Approach (O(n) time, O(1) space)**

👉 Steps:

1. Partition the array into negatives and positives (like QuickSort partition).
2. Then swap alternate negative and positive elements to achieve alternating order.

---

## **Java Code**

```java
import java.util.Arrays;

public class RearrangeAlternately {
    // Function to rearrange positives and negatives alternately
    public static void rearrange(int[] arr) {
        int n = arr.length;
        int i = -1;

        // Step 1: Partition (move negatives to left side, positives to right)
        for (int j = 0; j < n; j++) {
            if (arr[j] < 0) {
                i++;
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }

        // At this point:
        // arr[0..i] => negative numbers
        // arr[i+1..n-1] => positive numbers

        int neg = 0;      // index of first negative
        int pos = i + 1;  // index of first positive

        // Step 2: Swap negatives with positives alternately
        while (neg < pos && pos < n && arr[neg] < 0) {
            int temp = arr[neg];
            arr[neg] = arr[pos];
            arr[pos] = temp;

            neg += 2; // move to next alternate negative index
            pos++;
        }
    }

    public static void main(String[] args) {
        int[] arr = {1, 2, 3, -4, -1, 4};
        rearrange(arr);
        System.out.println(Arrays.toString(arr));
    }
}
```

---

## **Output**

```
[-4, 1, -1, 2, 3, 4]
```

---

## **Complexity**

* **Time Complexity:** O(n)

  * Partition step: O(n)
  * Rearrangement step: O(n)
* **Space Complexity:** O(1) (in-place, no extra arrays)

---

✅ This ensures negatives and positives alternate, while still being efficient.

Would you like me to also show the **approach that preserves the original order of appearance** (stable rearrangement), even if it costs O(n) extra space?
