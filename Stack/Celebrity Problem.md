Great question 👍 The **Celebrity Problem** is a **famous stack + matrix problem** often asked in interviews.

---

## 📌 Problem Statement:

You are given a **matrix M\[]\[]** of size `N x N` where:

* `M[i][j] = 1` means **person i knows person j**.
* `M[i][j] = 0` means **person i does not know person j**.

A **celebrity** is defined as:

1. Everyone knows the celebrity.
2. Celebrity knows no one.

👉 You have to find the index of the celebrity or return `-1` if none exists.

---

## 📌 Approaches

### **Approach 1: Brute Force (O(N²))**

* For each person, check if:

  1. They don’t know anyone (`M[i][j] == 0` for all j).
  2. Everyone knows them (`M[j][i] == 1` for all j).
* If both true → celebrity.

**Code (Brute Force):**

```java
public class CelebrityProblem {
    static int findCelebrity(int[][] M, int n) {
        for(int i = 0; i < n; i++) {
            boolean knowsNoOne = true;
            boolean everyoneKnows = true;

            // Check if person i knows anyone
            for(int j = 0; j < n; j++) {
                if(M[i][j] == 1) { 
                    knowsNoOne = false; 
                    break;
                }
            }

            // Check if everyone knows person i
            for(int j = 0; j < n; j++) {
                if(i != j && M[j][i] == 0) { 
                    everyoneKnows = false; 
                    break;
                }
            }

            if(knowsNoOne && everyoneKnows) return i;
        }
        return -1;
    }

    public static void main(String[] args) {
        int M[][] = {{0,1,0},
                     {0,0,0},
                     {0,1,0}};
        int n = 3;
        System.out.println(findCelebrity(M,n)); // Output: 1
    }
}
```

---

### **Approach 2: Stack Approach (O(N))**

* Push all people into a stack.
* Pop two persons `a` and `b`.

  * If `a` knows `b`, `a` can’t be a celebrity → push `b`.
  * Else `b` can’t be a celebrity → push `a`.
* At the end, only **one candidate** remains.
* Verify the candidate.

**Code (Stack Approach):**

```java
import java.util.*;

public class CelebrityProblem {
    static int findCelebrity(int[][] M, int n) {
        Stack<Integer> stack = new Stack<>();
        
        // Push all people into stack
        for(int i = 0; i < n; i++) {
            stack.push(i);
        }
        
        // Find potential celebrity
        while(stack.size() > 1) {
            int a = stack.pop();
            int b = stack.pop();
            
            if(M[a][b] == 1) {
                // a knows b → a is not celebrity
                stack.push(b);
            } else {
                // a doesn't know b → b is not celebrity
                stack.push(a);
            }
        }
        
        int candidate = stack.pop();
        
        // Verify candidate
        for(int i = 0; i < n; i++) {
            if(i != candidate) {
                if(M[candidate][i] == 1 || M[i][candidate] == 0) {
                    return -1;
                }
            }
        }
        return candidate;
    }

    public static void main(String[] args) {
        int M[][] = {{0,1,0},
                     {0,0,0},
                     {0,1,0}};
        int n = 3;
        System.out.println(findCelebrity(M,n)); // Output: 1
    }
}
```

---

### **Approach 3: Two-Pointer Elimination (Most Optimal, O(N))**

* Start with two pointers: `a = 0`, `b = n-1`.
* While `a < b`:

  * If `a` knows `b`, then `a` cannot be celebrity → `a++`.
  * Else `b` cannot be celebrity → `b--`.
* One candidate remains. Verify the candidate.

**Code (Two-Pointer):**

```java
public class CelebrityProblem {
    static int findCelebrity(int[][] M, int n) {
        int a = 0, b = n-1;
        
        while(a < b) {
            if(M[a][b] == 1) {
                a++; // a knows b → not celebrity
            } else {
                b--; // b cannot be celebrity
            }
        }
        
        // a is candidate
        for(int i = 0; i < n; i++) {
            if(i != a && (M[a][i] == 1 || M[i][a] == 0)) {
                return -1;
            }
        }
        return a;
    }

    public static void main(String[] args) {
        int M[][] = {{0,1,0},
                     {0,0,0},
                     {0,1,0}};
        int n = 3;
        System.out.println(findCelebrity(M,n)); // Output: 1
    }
}
```

---

## 📌 Topic:

This problem falls under:

* **Stack / Matrix Problems**
* **Elimination Techniques**
* **Greedy elimination + verification**

---

👉 Would you like me to **dry run the stack approach** step by step with an example matrix? That’s the one most interviewers ask about.
