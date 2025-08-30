Perfect choice 🍌😃 — **Koko Eating Bananas** is a very famous **Binary Search on Answer** problem. Let’s go step by step.

---

## 🔹 Problem: Koko Eating Bananas

Koko has `n` piles of bananas, where `piles[i]` is the number of bananas in the `i`th pile.
She can decide her eating speed `k` (bananas per hour).
Each hour, she chooses a pile and eats up to `k` bananas from that pile. If the pile has fewer than `k`, she eats all of them.
She must finish eating all bananas within `h` hours.

👉 Find the **minimum `k`** such that she can finish within `h`.

---

## 🔹 Approach

1. **Range of Speed:**

   * Minimum speed = `1` banana/hour.
   * Maximum speed = `max(piles)` bananas/hour (fastest way).

2. **Binary Search on Speed:**

   * For a mid-speed `k`, calculate how many hours Koko needs.
   * If total hours ≤ `h`, then `k` is possible → try smaller speed.
   * If total hours > `h`, then `k` is too small → increase speed.

3. **Time Complexity:**

   * Checking hours for one speed = `O(n)`
   * Binary Search range = `log(max(piles))`
   * Total = `O(n * log(max(piles)))`

4. **Space Complexity:** `O(1)`

---

## 🔹 Java Code

```java
public class KokoEatingBananas {
    
    // Function to check if Koko can finish with given speed
    private static boolean canEatAll(int[] piles, int h, int speed) {
        int hours = 0;
        for (int pile : piles) {
            // ceil(pile / speed)
            hours += (pile + speed - 1) / speed;
        }
        return hours <= h;
    }

    public static int minEatingSpeed(int[] piles, int h) {
        int left = 1;
        int right = 0;

        // Max pile = max speed needed
        for (int pile : piles) {
            right = Math.max(right, pile);
        }

        int ans = right;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            
            if (canEatAll(piles, h, mid)) {
                ans = mid; // valid speed, try smaller
                right = mid - 1;
            } else {
                left = mid + 1; // too slow
            }
        }
        return ans;
    }

    public static void main(String[] args) {
        int[] piles = {3, 6, 7, 11};
        int h = 8;
        System.out.println("Minimum eating speed: " + minEatingSpeed(piles, h));
    }
}
```

---

## 🔹 Input / Output

**Input:**

```
piles = [3,6,7,11], h = 8
```

**Output:**

```
Minimum eating speed: 4
```

👉 Explanation:

* If speed = 4 → \[1,2,2,3] hours = 8 ✅
* If speed = 3 → \[1,2,3,4] hours = 10 ❌

---

Do you want me to also give the **Python version** (very short & clean), or continue with the **next Binary Search on Answer problem** (like "Capacity to Ship Packages")?
