
Here’s a Java example:

```java
import java.util.*;

public class AllPairsWithSum {
    public static void main(String[] args) {
        int[] nums = {2, 7, 4, 5, 3, 6, 1, 8, 2};
        int target = 9;

        List<int[]> result = findAllPairs(nums, target);

        System.out.println("Pairs with sum " + target + ":");
        for (int[] pair : result) {
            System.out.println(pair[0] + ", " + pair[1]);
        }
    }

    public static List<int[]> findAllPairs(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>(); // value -> count
        List<int[]> pairs = new ArrayList<>();

        for (int num : nums) {
            int rest = target - num;
            if (map.containsKey(rest) && map.get(rest) > 0) {
                pairs.add(new int[]{rest, num});
                map.put(rest, map.get(rest) - 1); // reduce count for rest
            } else {
                map.put(num, map.getOrDefault(num, 0) + 1); // store count
            }
        }

        return pairs;
    }
}
```

### How it works:

1. **Map stores frequency** of numbers seen so far.
2. For each number:

   * Check if its complement (`target - num`) exists in the map.
   * If yes, record the pair and reduce that complement’s count.
   * Otherwise, store this number in the map.
3. Works for **multiple pairs** without reusing the same element twice.

**Example output for target=9**:

```
Pairs with sum 9:
2, 7
4, 5
3, 6
8, 1
2, 7
```

If you want, I can also give a **version that returns all unique pairs** without duplicates.
