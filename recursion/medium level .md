Perfect 🚀 You’re asking for the classic **recursion + backtracking set**:

* **Power of a number (x^n)**
* **Palindrome check**
* **Printing subsets of a string**
* **Tower of Hanoi**
* **N-Queens Problem**

Let’s go one by one in **Java**.

---

## 1️⃣ Power of a Number (x^n)

```java
public class Main {
    public static void main(String[] args) {
        int x = 2, n = 5;
        System.out.println(x + "^" + n + " = " + power(x, n));
    }

    public static int power(int x, int n) {
        // Base Case
        if (n == 0) return 1;
        // Recursive Case
        return x * power(x, n - 1);
    }
}
```

📌 Optimized (Divide & Conquer):
If n is even → `x^n = (x^(n/2)) * (x^(n/2))`
If n is odd → `x^n = x * (x^(n/2)) * (x^(n/2))`
Time Complexity: **O(log n)** instead of O(n).

---

## 2️⃣ Palindrome Check (using recursion)

```java
public class Main {
    public static void main(String[] args) {
        String str = "madam";
        System.out.println(str + " is palindrome? " + isPalindrome(str, 0, str.length() - 1));
    }

    public static boolean isPalindrome(String str, int l, int r) {
        // Base Case
        if (l >= r) return true;
        // Recursive Case
        if (str.charAt(l) != str.charAt(r)) return false;
        return isPalindrome(str, l + 1, r - 1);
    }
}
```

---

## 3️⃣ Printing Subsets of a String

```java
public class Main {
    public static void main(String[] args) {
        String str = "abc";
        printSubsets(str, "", 0);
    }

    public static void printSubsets(String str, String curr, int index) {
        // Base Case
        if (index == str.length()) {
            System.out.println(curr);
            return;
        }
        // Choice 1 → Include char
        printSubsets(str, curr + str.charAt(index), index + 1);
        // Choice 2 → Exclude char
        printSubsets(str, curr, index + 1);
    }
}
```

👉 For `abc`, output:

```
abc
ab
ac
a
bc
b
c
(empty string)
```

---

## 4️⃣ Tower of Hanoi

```java
public class Main {
    public static void main(String[] args) {
        int n = 3;
        towerOfHanoi(n, "A", "C", "B"); // from A → C using B
    }

    public static void towerOfHanoi(int n, String from, String to, String aux) {
        if (n == 0) return;

        // Move n-1 disks from source to aux
        towerOfHanoi(n - 1, from, aux, to);

        // Move nth disk from source to destination
        System.out.println("Move disk " + n + " from " + from + " to " + to);

        // Move n-1 disks from aux to destination
        towerOfHanoi(n - 1, aux, to, from);
    }
}
```

---

## 5️⃣ N-Queens Problem (Backtracking)

```java
public class Main {
    static int N = 4;

    public static void main(String[] args) {
        int[][] board = new int[N][N];
        if (solveNQueens(board, 0)) {
            printBoard(board);
        } else {
            System.out.println("No solution exists");
        }
    }

    static boolean solveNQueens(int[][] board, int col) {
        if (col >= N) return true;

        for (int i = 0; i < N; i++) {
            if (isSafe(board, i, col)) {
                board[i][col] = 1;
                if (solveNQueens(board, col + 1)) return true;
                board[i][col] = 0; // Backtrack
            }
        }
        return false;
    }

    static boolean isSafe(int[][] board, int row, int col) {
        // Check left row
        for (int i = 0; i < col; i++)
            if (board[row][i] == 1) return false;

        // Check upper-left diagonal
        for (int i = row, j = col; i >= 0 && j >= 0; i--, j--)
            if (board[i][j] == 1) return false;

        // Check lower-left diagonal
        for (int i = row, j = col; i < N && j >= 0; i++, j--)
            if (board[i][j] == 1) return false;

        return true;
    }

    static void printBoard(int[][] board) {
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                System.out.print((board[i][j] == 1 ? "Q " : ". "));
            }
            System.out.println();
        }
    }
}
```

👉 Output for `N=4`:

```
. Q . .
. . . Q
Q . . .
. . Q .
```

---

⚡ These 5 cover **recursion basics → subsets → backtracking**.
Do you want me to now **explain their time complexities** (interview style), or move on to **more advanced backtracking** like *Word Search, Rat in a Maze, Sudoku Solver*?
