
### **Java Code for Left and Right Rotation**

```java
import java.util.Arrays;

public class Main {

    // Reverse part of array from start to end
    public static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }

    // Left rotate array by d positions
    public static void leftRotate(int[] arr, int d) {
        int n = arr.length;
        d = d % n;  // handle d > n
        reverse(arr, 0, d - 1);    // reverse first d elements
        reverse(arr, d, n - 1);    // reverse rest
        reverse(arr, 0, n - 1);    // reverse whole array
    }

    // Right rotate array by d positions
    public static void rightRotate(int[] arr, int d) {
        int n = arr.length;
        d = d % n;  // handle d > n
        reverse(arr, 0, n - 1);    // reverse whole array
        reverse(arr, 0, d - 1);    // reverse first d elements
        reverse(arr, d, n - 1);    // reverse rest
    }

    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3, 4, 5, 6};
        int d = 2;

        leftRotate(arr1, d);
        System.out.println("Left rotated by " + d + ": " + Arrays.toString(arr1));

        int[] arr2 = {1, 2, 3, 4, 5, 6};
        rightRotate(arr2, d);
        System.out.println("Right rotated by " + d + ": " + Arrays.toString(arr2));
    }
}
```

---

### **Output**

```
Left rotated by 2: [3, 4, 5, 6, 1, 2]
Right rotated by 2: [5, 6, 1, 2, 3, 4]
```

---

✅ **Key Notes**

* Right rotation by `d` is equivalent to **left rotation by `n - d`**.
* Time Complexity: **O(n)**
* Space Complexity: **O(1)** (in-place rotation)

---

If you want, I can also give a **brute-force simpler version using loops** which is easier to understand for beginners.

Do you want me to do that?
