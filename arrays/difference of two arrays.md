Ah! Got it ✅ You want the **difference of two arrays in both directions**, **formatted as two lists**:

* First list = `nums1 - nums2`
* Second list = `nums2 - nums1`

---

### ✅ Java Code

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        int[] nums1 = {1, 2, 3};
        int[] nums2 = {2, 4, 6};

        // Convert nums2 to HashSet for O(1) lookup
        Set<Integer> set2 = new HashSet<>();
        for (int num : nums2) set2.add(num);

        // nums1 - nums2
        List<Integer> diff1 = new ArrayList<>();
        for (int num : nums1) {
            if (!set2.contains(num)) diff1.add(num);
        }

        // Convert nums1 to HashSet for O(1) lookup
        Set<Integer> set1 = new HashSet<>();
        for (int num : nums1) set1.add(num);

        // nums2 - nums1
        List<Integer> diff2 = new ArrayList<>();
        for (int num : nums2) {
            if (!set1.contains(num)) diff2.add(num);
        }

        // Output as list of lists
        List<List<Integer>> result = new ArrayList<>();
        result.add(diff1);
        result.add(diff2);

        System.out.println(result);
    }
}
```

---

### ✅ Output

```
[[1, 3], [4, 6]]
```

---

### ✅ Complexity

* **Time:** O(n + m) → scanning both arrays once
* **Space:** O(n + m) → for HashSets + output lists

---

If you want, I can also show a **sorted arrays version** that does **this in O(1) extra space** using **two pointers**.

Do you want me to show that optimized version too?
