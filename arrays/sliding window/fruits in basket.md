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
// Sliding Window: O(n)
import java.util.*;

public class FruitIntoBasket {
    public static int totalFruit(int[] fruits) {
        int left = 0, right = 0;
        int maxLen = 0;
        Map<Integer, Integer> map = new HashMap<>(); // fruit -> count

        while (right < fruits.length) {
            // include current fruit
            map.put(fruits[right], map.getOrDefault(fruits[right], 0) + 1);

            // if more than 2 types, shrink window
            while (map.size() > 2) {
                map.put(fruits[left], map.get(fruits[left]) - 1);
                if (map.get(fruits[left]) == 0) {
                    map.remove(fruits[left]);
                }
                left++;
            }

            // update max window length
            maxLen = Math.max(maxLen, right - left + 1);

            right++;
        }
        return maxLen;
    }

    public static void main(String[] args) {
        int[] fruits = {1, 2, 1, 2, 3};
        System.out.println("Max Fruits Collected = " + totalFruit(fruits));
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
