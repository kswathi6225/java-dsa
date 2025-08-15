
# 🔍 Single Element in a Sorted Array (Binary Search)

## 🧠 Problem Statement:
Given a sorted array where every element appears exactly twice **except one element**, which appears only once. Find that single element using **binary search**.

### ✅ Constraints:
- The array is **sorted**
- All elements appear twice **except one**
- Goal is to find that unique element in **O(log n)** time using binary search

---

## 💡 Approach (Binary Search):
1. Use a modified binary search to locate the unique element.
2. Observe that:
   - Elements before the single element will follow the pattern: first occurrence at even index, second at odd.
   - After the single element, this pattern breaks.
3. Use `mid` and check whether the element pairs are in proper pattern.
4. Narrow search space accordingly.

---

## 🧾 java Code

```java
public class SingleElement {
    public static int singleNonDuplicate(int[] nums) {
        int start = 0, end = nums.length - 1;

        while (start <= end) {
            int mid = start + (end - start) / 2;

            // Check if mid is the single element
            if ((mid == 0 || nums[mid] != nums[mid - 1]) &&
                (mid == nums.length - 1 || nums[mid] != nums[mid + 1])) {
                return nums[mid];
            }

            // Adjust mid to the first element of the pair
            if (mid > 0 && nums[mid] == nums[mid - 1]) {
                mid--;
            }

            // If mid is even, single element is on the right
            if (mid % 2 == 0) {
                start = mid + 2;
            } else {
                end = mid - 1;
            }
        }

        return -1; // Should never be reached
    }

    public static void main(String[] args) {
        int[] nums = {1, 1, 2, 3, 3, 4, 4, 8, 8};
        System.out.println("Single element: " + singleNonDuplicate(nums));
    }
}

````

---

## 🧪 Input

```cpp
nums = {1, 1, 2, 3, 3, 4, 4, 8, 8};
```

## 📤 Output

```
Single element: 2
```

---
MORE OPTIMIZED METHOD SMALL IN BOOK

## ⏱️ Time Complexity:

* **O(log n)** due to binary search
* **O(1)** space

---

## ✅ Notes:

* The key trick is to use the parity of indices and pairing pattern.
* Be cautious about array bounds when accessing `nums[mid±1]`.

```
