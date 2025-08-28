Perfect 👍 Let’s write **Markdown + Code (Java + Python)** for all 3 cases you asked:

---

# 🟢 Pascal’s Triangle Problems

---

## 1️⃣ Given Row (R) and Column (C), find element at that place

Formula:

$$
\text{Element} = \binom{R-1}{C-1} = \frac{(R-1)!}{(C-1)! \cdot (R-C)!}
$$

### Example: R=5, C=3 → $\binom{4}{2} = 6$

### **Java**

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
        System.out.println("Element at R=" + R + ", C=" + C + " is: " + nCr(R - 1, C - 1));
    }
}
```

✅ Output: `6`

---

## 2️⃣ Print any given row of Pascal’s Triangle (n = 5)

Row 5 → `[1, 4, 6, 4, 1]`

### **Java**

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
``

✅ Output: `1 4 6 4 1`

---

## 3️⃣ Print Complete Pascal’s Triangle (till n rows)

### **Java**

```java
public class PascalsTriangle {
    static void printTriangle(int n) {
        for (int i = 0; i < n; i++) {
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

✅ Output (for n=5):

```
1 
1 1 
1 2 1 
1 3 3 1 
1 4 6 4 1
```

---

👉 Do you want me to also give you the **optimized DP approach (using lists/arrays)** for generating Pascal’s triangle (used in interview problems like "Leetcode Pascal’s Triangle")?
