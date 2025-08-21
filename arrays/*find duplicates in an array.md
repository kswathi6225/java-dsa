Perfect 👍 Let’s write Java code to **find duplicates in an array**.

---

### ✅ Method 1: Using `HashSet`

This is the most common and efficient way.

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 2, 5, 6, 1, 3};

        Set<Integer> seen = new HashSet<>();
        Set<Integer> duplicates = new HashSet<>();

        for (int num : arr) {
            if (!seen.add(num)) { // if already exists in 'seen'
                duplicates.add(num);
            }
        }

        System.out.println("Duplicates: " + duplicates);
    }
}
```

✅ Output:

```
Duplicates: [1, 2, 3]
```

---

### ✅ Method 2: Using Nested Loops (Brute Force)

(not efficient but easy to understand)

```java
public class Main {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 2, 5, 6, 1, 3};

        System.out.print("Duplicates: ");
        for (int i = 0; i < arr.length; i++) {
            for (int j = i + 1; j < arr.length; j++) {
                if (arr[i] == arr[j]) {
                    System.out.print(arr[i] + " ");
                    break;
                }
            }
        }
    }
}
```

✅ Output:

```
Duplicates: 1 2 3
```

---

👉 The **HashSet method** is better because it runs in **O(n)** time, while the nested loop method is **O(n²)**.

Do you also want me to show the **frequency of each element** (like a count dictionary in Python)?
