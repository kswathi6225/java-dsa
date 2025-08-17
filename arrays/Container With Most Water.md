
# 🪣 Container With Most Water – Java Solutions

### 🧠 **Problem Statement (Leetcode 11):**

Given `n` non-negative integers `height[0], height[1], ..., height[n-1]`, where each value represents the height of a vertical line on the x-axis at index `i`,
Find two lines that together with the x-axis form a container, such that the container holds the **most water**.

---

### 📥 Example Input:

```cpp
height = [1,8,6,2,5,4,8,3,7]
```

### 📤 Output:

```
49
```

## **Approach 1 – Naive (Brute Force)**

**Idea:**
Check **all possible pairs** of lines `(i, j)` and calculate water = `min(arr[i], arr[j]) * (j - i)`.
Keep track of the maximum water found.

**Time Complexity:** `O(n²)`
**Space Complexity:** `O(1)`

```java
public class Main {
    public static int mswt(int[] height) {
        int maxwater = 0;
        int ht, width;

        for (int i = 0; i < height.length; i++) {
            for (int j = i + 1; j < height.length; j++) {
                ht = Math.min(height[i], height[j]);
                width = j - i;
                int area = ht * width;
                maxwater = Math.max(maxwater, area);
            }
        }

        return maxwater;
    }

    public static void main(String[] args) {
        int[] height = {1, 8, 6, 2, 5, 4, 8, 3, 7};
        int maxwater = mswt(height);
        System.out.println("Max water : " + maxwater);
    }
}

```

---

## **Approach 2 – Two Pointers (Optimized)**

**Idea:**

* Use two pointers: one at the start (`left`) and one at the end (`right`).
* Calculate the water between them.
* Move the pointer that points to the **shorter line**, since moving the taller line won’t help increase height but will reduce width.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(1)`

```java
public class Main {
    public static int mswt(int[] height) {
        int n = height.length;
        int lp = 0;          // left pointer
        int rp = n - 1;      // right pointer
        int maxwater = 0;

        while (lp < rp) {
            int w = rp - lp;
            int ht = Math.min(height[lp], height[rp]);
            int curwater = w * ht;
            maxwater = Math.max(maxwater, curwater);

            if (height[lp] < height[rp])
                lp++;
            else
                rp--;
        }

        return maxwater;  // ✅ return result
    }
    public static void main(String[] args) {
        int[] height = {1, 8, 6, 2, 5, 4, 8, 3, 7};
        int maxwater = mswt(height);
        System.out.println("Max water : " + maxwater);
    }
}

```

---

✅ **Recommendation:** Always use the **Two Pointer** method for this problem—it’s much faster than brute force.

---

Do you want me to also **draw a visual diagram** in the Markdown so the container logic becomes intuitive? That would make it easier to remember.
