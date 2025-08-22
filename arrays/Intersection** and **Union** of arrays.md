
### **Union**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3, 4};
        int[] arr2 = {3, 4, 5, 6};

        Set<Integer> union = new HashSet<>();
        for (int num : arr1) union.add(num);
        for (int num : arr2) union.add(num);

        System.out.println("Union: " + union);
    }
}
```

**Output:**

```
Union: [1, 2, 3, 4, 5, 6]
```

### **Intersection**

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] arr1 = {1, 2, 3, 4};
        int[] arr2 = {3, 4, 5, 6};

        Set<Integer> set1 = new HashSet<>();
        for (int num : arr1) set1.add(num);

        Set<Integer> intersection = new HashSet<>();
        for (int num : arr2) {
            if (set1.contains(num)) {
                intersection.add(num);
            }
        }

        System.out.println("Intersection: " + intersection);
    }
}
```

**Output:**

```
Intersection: [3, 4]
```

---

### **✅ Complexity**

* **Time Complexity:** O(n + m)
* **Space Complexity:** O(n + m) (for sets)

---

If you want, I can also show a \*\*solution for intersection/union of **sorted arrays without using extra space**, which is very efficient for interviews.

Do you want me to do that?
