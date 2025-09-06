Ah! The problem **“Maximum Sum Rectangle in a 2D Matrix”** is slightly **above easy level**—it’s usually considered **medium** on LeetCode, because it requires an optimized approach using Kadane’s algorithm for 2D matrices. But I can explain it clearly so you can handle it in interviews.

---

## Problem Statement

Given a 2D matrix of integers (can be negative), find the **rectangle (submatrix) with the maximum sum**.

**Example:**

```text
Input:
matrix = [
  [1,  2, -1, -4, -20],
  [-8, -3, 4, 2, 1],
  [3,  8, 10, 1, 3],
  [-4, -1, 1, 7, -6]
]

Output: 29
```

The maximum sum rectangle is:

```text
[
  [3, 8, 10],
  [-4, -1, 1]
]
```

---

## Approach (Optimal – Kadane’s for 2D)

1. **Fix the left and right columns** of the rectangle.
2. **Collapse the 2D matrix to 1D** for these columns by summing row elements between the left and right columns.
3. **Apply Kadane’s algorithm** on this 1D array to find the maximum sum subarray (gives top and bottom row).
4. **Repeat for all pairs of columns** and track the maximum sum found.

**Time Complexity:** O(cols² \* rows)
**Space Complexity:** O(rows)

---

## Python Code

```python
def maxSumRectangle(matrix):
    if not matrix: return 0
    rows, cols = len(matrix), len(matrix[0])
    max_sum = float('-inf')
    
    for left in range(cols):
        temp = [0] * rows
        
        for right in range(left, cols):
            # Sum rows between left and right columns
            for i in range(rows):
                temp[i] += matrix[i][right]
            
            # Apply Kadane's algorithm on temp
            current_sum = temp[0]
            max_ending = temp[0]
            for i in range(1, rows):
                max_ending = max(temp[i], max_ending + temp[i])
                current_sum = max(current_sum, max_ending)
            
            max_sum = max(max_sum, current_sum)
    
    return max_sum

# Example usage
matrix = [
  [1, 2, -1, -4, -20],
  [-8, -3, 4, 2, 1],
  [3, 8, 10, 1, 3],
  [-4, -1, 1, 7, -6]
]
print(maxSumRectangle(matrix))  # Output: 29
```

---

This is the **most efficient approach** for 2D maximum sum submatrix for arbitrary integers.

If you want, I can also **draw a visual diagram** showing how the left/right columns + Kadane collapse works—it really helps in interviews.

Do you want me to do that?
