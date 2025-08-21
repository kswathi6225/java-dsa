Got it 👍 Let’s write the **same reverse array code in Java** (both in-place and using an extra array).
I’ll also add **time & space complexity** for both.

---

### 🔹 Method 1: In-place two-pointer swap

```java
import java.util.Arrays;

public class ReverseArray {
    public static int[] rev(int[] arr) {
        int i = 0, j = arr.length - 1;
        while (i < j) {
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
            i++;
            j--;
        }
        return arr; // returns the reversed array
    }

    public static void main(String[] args) {
        int[] array = {1, 2, 3, 4, 5};
        System.out.println(Arrays.toString(rev(array))); // [5, 4, 3, 2, 1]
    }
}
```

✅ **Time Complexity:** O(n)
✅ **Space Complexity:** O(1) (in-place)

---

### 🔹 Method 2: Using extra array (like slicing in Python)

```java
import java.util.Arrays;

public class ReverseArray {
    public static int[] rev1(int[] arr) {
        int n = arr.length;
        int[] result = new int[n];
        for (int i = 0; i < n; i++) {
            result[i] = arr[n - i - 1];
        }
        return result;
    }

    public static void main(String[] args) {
        int[] array = {1, 2, 3, 4, 5};
        System.out.println(Arrays.toString(rev1(array))); // [5, 4, 3, 2, 1]
    }
}
```

✅ **Time Complexity:** O(n)
✅ **Space Complexity:** O(n) (new array created)

---

📌 Summary:

| Method      | Time Complexity | Space Complexity |
| ----------- | --------------- | ---------------- |
| Two-pointer | O(n)            | O(1)             |
| Extra array | O(n)            | O(n)             |

---

Do you want me to also give the **recursive approach** in both Java & Python for reversal (with complexities) so your notes are 100% complete?
