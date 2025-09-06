Perfect! 🚀 Since you’ve mastered **basic matrix problems**, let’s move to the **next set: intermediate/medium-level matrix problems**. These are commonly asked in interviews and coding tests.

I’ll give the **problem, explanation, input/output**, and **Java code** for each.

---

# 🟢 Intermediate Matrix Problems

## 1️⃣ Spiral Traversal of a Matrix

**Problem:** Print matrix elements in a **spiral order** (clockwise).

```
Input:
1 2 3
4 5 6
7 8 9

Output: 1 2 3 6 9 8 7 4 5
```

```java
public class SpiralMatrix {
    public static void main(String[] args) {
        int[][] mat = {
            {1,2,3},
            {4,5,6},
            {7,8,9}
        };
        int top = 0, bottom = mat.length - 1;
        int left = 0, right = mat[0].length - 1;

        System.out.println("Spiral Order:");
        while (top <= bottom && left <= right) {
            // Top row
            for (int j = left; j <= right; j++) System.out.print(mat[top][j] + " ");
            top++;
            // Right column
            for (int i = top; i <= bottom; i++) System.out.print(mat[i][right] + " ");
            right--;
            // Bottom row
            if (top <= bottom) {
                for (int j = right; j >= left; j--) System.out.print(mat[bottom][j] + " ");
                bottom--;
            }
            // Left column
            if (left <= right) {
                for (int i = bottom; i >= top; i--) System.out.print(mat[i][left] + " ");
                left++;
            }
        }
    }
}
```

---

## 2️⃣ Rotate Matrix 90° Clockwise

**Problem:** Rotate a square matrix by 90° clockwise in place.

```
Input:
1 2 3
4 5 6
7 8 9

Output:
7 4 1
8 5 2
9 6 3
```

```java
public class RotateMatrix {
    public static void main(String[] args) {
        int[][] mat = {
            {1,2,3},
            {4,5,6},
            {7,8,9}
        };
        int n = mat.length;

        // Transpose
        for (int i = 0; i < n; i++)
            for (int j = i; j < n; j++)
                { int temp = mat[i][j]; mat[i][j] = mat[j][i]; mat[j][i] = temp; }

        // Reverse each row
        for (int i = 0; i < n; i++) {
            int l = 0, r = n - 1;
            while (l < r) { int temp = mat[i][l]; mat[i][l] = mat[i][r]; mat[i][r] = temp; l++; r--; }
        }

        System.out.println("90° Rotated Matrix:");
        for (int[] row : mat) {
            for (int val : row) System.out.print(val + " ");
            System.out.println();
        }
    }
}
```

---

## 3️⃣ Boundary Traversal

**Problem:** Print all boundary elements of a matrix.

```
Input:
1 2 3
4 5 6
7 8 9

Output: 1 2 3 6 9 8 7 4
```

```java
public class BoundaryTraversal {
    public static void main(String[] args) {
        int[][] mat = {
            {1,2,3},
            {4,5,6},
            {7,8,9}
        };
        int rows = mat.length, cols = mat[0].length;

        // Top row
        for(int j=0;j<cols;j++) System.out.print(mat[0][j]+" ");
        // Right column
        for(int i=1;i<rows;i++) System.out.print(mat[i][cols-1]+" ");
        // Bottom row
        for(int j=cols-2;j>=0;j--) System.out.print(mat[rows-1][j]+" ");
        // Left column
        for(int i=rows-2;i>0;i--) System.out.print(mat[i][0]+" ");
    }
}
```

---

## 4️⃣ Search in Sorted Matrix

**Problem:** Search a number in a **row-wise and column-wise sorted matrix** efficiently.

```
Input:
1 3 5
2 4 7
6 8 9
Target = 4
Output: Found at (1,1)
```

```java
public class SearchSortedMatrix {
    public static void main(String[] args) {
        int[][] mat = {
            {1,3,5},
            {2,4,7},
            {6,8,9}
        };
        int target = 4;
        int row = 0, col = mat[0].length - 1;
        boolean found = false;

        while(row < mat.length && col >= 0) {
            if(mat[row][col] == target) { found = true; break; }
            else if(mat[row][col] > target) col--;
            else row++;
        }

        if(found) System.out.println("Found at (" + row + "," + col + ")");
        else System.out.println("Not Found");
    }
}
```

---

## 5️⃣ Count Number of Elements Greater than X

**Problem:** Count how many elements in the matrix are greater than a given number X.

```
Input: mat = [[1,2],[3,4]], X=2
Output: 2
```

```java
public class CountGreater {
    public static void main(String[] args) {
        int[][] mat = {{1,2},{3,4}};
        int X = 2;
        int count = 0;

        for(int i=0;i<mat.length;i++)
            for(int j=0;j<mat[0].length;j++)
                if(mat[i][j] > X) count++;

        System.out.println("Count = " + count);
    }
}
```

---

✨ That’s a good **next level set of 5 intermediate matrix problems**.
We can continue next with **even harder ones** like:

* Diagonal Traverse
* Rotate Matrix 180°
* Maximum Sum Submatrix
* Spiral Fill

---

Do you want me to go ahead and **code those advanced matrix problems next**?
