Sure! Let’s go over **Longest Happy Prefix** — a classic string problem often solved using **KMP (prefix function)**.

---

## **Problem:** Longest Happy Prefix

A **happy prefix** of a string is a prefix which is also a **suffix**, but **not the entire string**.

**Goal:** Find the **longest happy prefix**.

---

### **Example**

**Input:** `"level"`

* Prefixes: `"l"`, `"le"`, `"lev"`, `"leve"`
* Suffixes: `"l"`, `"el"`, `"vel"`, `"evel"`
* Longest happy prefix = `"l"`

**Input:** `"ababab"`

* Longest happy prefix = `"abab"`

---

## **Optimal Approach (KMP Prefix Function)**

1. Use a **prefix function** (like in KMP) to find the longest proper prefix which is also a suffix.
2. The last value of the prefix array gives the length of the longest happy prefix.

**Time Complexity:** `O(n)`
**Space Complexity:** `O(n)`

---

### **Java Code**

```java
public class LongestHappyPrefix {

    public static String longestPrefix(String s) {
        int n = s.length();
        int[] lps = new int[n]; // longest prefix suffix array
        int len = 0; // length of the previous longest prefix suffix

        // i starts from 1
        for (int i = 1; i < n; i++) {
            while (len > 0 && s.charAt(i) != s.charAt(len)) {
                len = lps[len - 1];
            }
            if (s.charAt(i) == s.charAt(len)) {
                len++;
                lps[i] = len;
            }
        }

        // The last value in lps array is the length of longest happy prefix
        return s.substring(0, lps[n - 1]);
    }

    public static void main(String[] args) {
        String str = "ababab";
        System.out.println("Longest Happy Prefix: " + longestPrefix(str)); // Output: "abab"

        str = "level";
        System.out.println("Longest Happy Prefix: " + longestPrefix(str)); // Output: "l"
    }
}
```

---

### **How it works (dry run example `"ababab"`):**

* Initialize `lps = [0,0,0,0,0,0]`

* i=1 → `s[1]='b'`, s\[0]='a' → no match → lps\[1]=0

* i=2 → `s[2]='a'`, s\[0]='a' → match → len=1 → lps\[2]=1

* i=3 → `s[3]='b'`, s\[1]='b' → match → len=2 → lps\[3]=2

* i=4 → `s[4]='a'`, s\[2]='a' → match → len=3 → lps\[4]=3

* i=5 → `s[5]='b'`, s\[3]='b' → match → len=4 → lps\[5]=4

* Last value = `lps[5]=4` → `"abab"` is the longest happy prefix.

---

If you want, I can also show a **simpler brute-force approach** for understanding before moving to KMP.

Do you want me to do that?
