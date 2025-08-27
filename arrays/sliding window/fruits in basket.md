## TWO POINTERS AND SLIDING WINDOW

# 🍎 Problem: Fruit Into Baskets

### Problem Statement

You are given an array `fruits[]` where `fruits[i]` represents the type of fruit at index `i`.
You have **two baskets**, and each basket can only hold **one type of fruit**.

You want to collect the **maximum number of fruits** by choosing a subarray where there are **at most 2 distinct fruit types**.

Return the **length of the longest such subarray**.

---

## ✅ Example

### Input

```
fruits = [1, 2, 1]
```

### Output

```
3
```

**Explanation:** You can take all 3 fruits → types {1,2}.

---

### Input

```
fruits = [0,1,2,2]
```

### Output

```
3
```

**Explanation:** Longest subarray is `[1,2,2]` (types {1,2}).

---

### Input

```
fruits = [1,2,3,2,2]
```

### Output

```
4
```

**Explanation:** Longest subarray is `[2,3,2,2]`.

---

---

# 🛠 Approaches

---

## Approach 1: Brute Force (Check all subarrays)

* Generate all subarrays.
* Check if it has at most 2 distinct fruits.
* Track max length.

### Code (Brute Force - Python)

```python
def totalFruit(fruits):
    n = len(fruits)
    max_len = 0
    
    for i in range(n):
        distinct = set()
        for j in range(i, n):
            distinct.add(fruits[j])
            if len(distinct) <= 2:
                max_len = max(max_len, j - i + 1)
            else:
                break
    return max_len

# Example
print(totalFruit([1,2,1]))  # Output: 3
```

⏱ Time Complexity: **O(n²)**
📦 Space Complexity: **O(1)** (set at most size 3).

---

## Approach 2: Sliding Window + HashMap (Optimal ✅)

### Intuition

* Use a window `[left, right]`.
* Store counts of fruits in a HashMap.
* If we have >2 distinct fruits → shrink from left.
* Track max window size.

---

### Code (Optimal - Java)

```java
import java.util.*;

public class FruitIntoBaskets {
    public static int totalFruit(int[] fruits) {
        Map<Integer, Integer> count = new HashMap<>();
        int left = 0, maxLen = 0;

        for (int right = 0; right < fruits.length; right++) {
            count.put(fruits[right], count.getOrDefault(fruits[right], 0) + 1);

            while (count.size() > 2) {
                count.put(fruits[left], count.get(fruits[left]) - 1);
                if (count.get(fruits[left]) == 0) {
                    count.remove(fruits[left]);
                }
                left++;
            }
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }

    public static void main(String[] args) {
        System.out.println(totalFruit(new int[]{1,2,1}));      // 3
        System.out.println(totalFruit(new int[]{0,1,2,2}));    // 3
        System.out.println(totalFruit(new int[]{1,2,3,2,2}));  // 4
    }
}
```

---

⏱ Time Complexity: **O(n)** (each element enters/leaves window once).
📦 Space Complexity: **O(1)** (map stores at most 3 fruits).

---

## 🔑 Key Learning

* This is the **same as Longest Subarray with at most K distinct elements (K=2 here)**.
* A **classic sliding window problem** you’ll use again in:

  * Longest substring with K distinct chars
  * Subarray with at most K odd numbers
  * Max consecutive 1s with K flips

---

👉 Do you want me to also give you a **dry run diagram** for one test case (\[1,2,3,2,2]) so it’s crystal clear how the sliding window works?
