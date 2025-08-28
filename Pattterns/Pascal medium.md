# 🟢 Pascal’s Triangle with 2D `ArrayList`

---

## 1️⃣ Generate Pascal’s Triangle (LeetCode Pascal’s Triangle I)

### **Java Code**

```java
import java.util.*;

public class PascalsTriangleList {
    static List<List<Integer>> generate(int numRows) {
        List<List<Integer>> triangle = new ArrayList<>();

        for (int i = 0; i < numRows; i++) {
            List<Integer> row = new ArrayList<>();
            int num = 1;
            for (int j = 0; j <= i; j++) {
                row.add(num);
                num = num * (i - j) / (j + 1);
            }
            triangle.add(row);
        }
        return triangle;
    }

    public static void main(String[] args) {
        int n = 5;
        List<List<Integer>> pascal = generate(n);

        // Printing the triangle
        for (List<Integer> row : pascal) {
            System.out.println(row);
        }
    }
}
```

### **Input**

```
n = 5
```

### **Output**

```
[1]
[1, 1]
[1, 2, 1]
[1, 3, 3, 1]
[1, 4, 6, 4, 1]
```

### **Complexity**

* **Time:** `O(n²)` (we generate all rows)
* **Space:** `O(n²)` (we store all rows in a 2D list)

---

## 2️⃣ Get the K-th Row (LeetCode Pascal’s Triangle II)

### **Java Code**

```java
import java.util.*;

public class PascalsRowList {
    static List<Integer> getRow(int rowIndex) {
        List<Integer> row = new ArrayList<>();
        long num = 1;
        for (int i = 0; i <= rowIndex; i++) {
            row.add((int) num);
            num = num * (rowIndex - i) / (i + 1);
        }
        return row;
    }

    public static void main(String[] args) {
        int k = 4;  // 0-based index -> Row 4 = [1, 4, 6, 4, 1]
        List<Integer> row = getRow(k);
        System.out.println("Row " + (k + 1) + ": " + row);
    }
}
```

### **Input**

```
k = 4
```

### **Output**

```
Row 5: [1, 4, 6, 4, 1]
```

### **Complexity**

* **Time:** `O(k)` (we compute row directly)
* **Space:** `O(1)` (ignoring output list)

---

## 3️⃣ Get an Element at Row R, Col C

Instead of recomputing factorials, we can use the same **nCr formula** as before, but wrap in a function.

### **Java Code**

```java
public class PascalsElementList {
    static int nCr(int n, int r) {
        int res = 1;
        for (int i = 0; i < r; i++) {
            res = res * (n - i) / (i + 1);
        }
        return res;
    }

    public static void main(String[] args) {
        int R = 5, C = 3;
        System.out.println("Element at Row " + R + ", Col " + C + " = " + nCr(R - 1, C - 1));
    }
}
```

### **Input**

```
R = 5, C = 3
```

### **Output**

```
Element at Row 5, Col 3 = 6
```

### **Complexity**

* **Time:** `O(C)`
* **Space:** `O(1)`

---

✅ Now you have **all 3 versions** (print, store in 2D list, access rows/elements) just like in coding interviews & LeetCode.

👉 Do you want me to also give a **Dynamic Programming approach** (storing each row from previous one instead of using formula) — that’s another common way interviewers expect for Pascal’s Triangle?
