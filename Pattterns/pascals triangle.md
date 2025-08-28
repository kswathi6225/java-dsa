# 🟢 Pascal’s Triangle Problems in Java

---

## 1️⃣ Find element at given Row (R) and Column (C)

**Formula:**

$$
\text{Element} = \binom{R-1}{C-1} = \frac{(R-1)!}{(C-1)! \cdot (R-C)!}
$$

### **Java Code**

```java
public class PascalsElement {
    static int nCr(int n, int r) {
        int res = 1;
        for (int i = 0; i < r; i++) {
            res = res * (n - i) / (i + 1);
        }
        return res;
    }

    public static void main(String[] args) {
        int R = 5, C = 3;
        int element = nCr(R - 1, C - 1);
        System.out.println("Element at Row " + R + ", Col " + C + " = " + element);
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

* **Time:** `O(C)` (since we compute nCr iteratively)
* **Space:** `O(1)`

---

## 2️⃣ Print any given row of Pascal’s Triangle (Row = n)

### **Java Code**

```java
public class PascalsRow {
    static void printRow(int n) {
        int num = 1;
        for (int i = 0; i < n; i++) {
            System.out.print(num + " ");
            num = num * (n - 1 - i) / (i + 1);
        }
    }

    public static void main(String[] args) {
        int n = 5;
        System.out.print("Row " + n + ": ");
        printRow(n);
    }
}
```

### **Input**

```
n = 5
```

### **Output**

```
Row 5: 1 4 6 4 1
```

### **Complexity**

* **Time:** `O(n)` (each element of the row is computed once)
* **Space:** `O(1)`

---

## 3️⃣ Print Complete Pascal’s Triangle (till n rows)

### **Java Code**

```java
public class PascalsTriangle {
    static void printTriangle(int n) {
        for (int i = 0; i < n; i++) {
            // spaces for triangle structure
            for (int s = 0; s < n - i; s++) {
                System.out.print(" ");
            }
            int num = 1;
            for (int j = 0; j <= i; j++) {
                System.out.print(num + " ");
                num = num * (i - j) / (j + 1);
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        int n = 5;
        printTriangle(n);
    }
}
```

### **Input**

```
n = 5
```

### **Output**

```
     1 
    1 1 
   1 2 1 
  1 3 3 1 
 1 4 6 4 1 
```

### **Complexity**

* **Time:** `O(n²)` (we print all elements of the triangle)
* **Space:** `O(1)` (no extra storage used)

---

👉 Do you also want me to extend this to **storing Pascal’s triangle in a 2D `ArrayList` (like in Leetcode “Pascal’s Triangle I & II”)** so you can reuse rows later, not just print them?
