# Longest Common Prefix using Sorting

## Problem Statement
Find the longest common prefix among an array of strings using the **sorting approach**.

---

## Java Code

```java
// Java program to find the longest common prefix
// using Sorting
import java.util.Arrays;

class GfG {
  
    static String longestCommonPrefix(String[] arr){
      
        // Sort the array of strings
        Arrays.sort(arr);

        // Get the first and last strings after sorting
        String first = arr[0];
        String last = arr[arr.length - 1];
        int minLength = Math.min(first.length(), last.length());
        
        // Find the common prefix between the first and last strings
        int i = 0;
        while (i < minLength && first.charAt(i) == last.charAt(i)) {
            i++;
        }

        // Return the common prefix
        return first.substring(0, i);
    }

    public static void main(String[] args){
        String[] arr = { "geeksforgeeks", "geeks", "geek", "geezer" };
        System.out.println(longestCommonPrefix(arr));
    }
}
````

---

## Input

```
arr = { "geeksforgeeks", "geeks", "geek", "geezer" }
```

## Output

```
gee
```

---

## Time Complexity

* Sorting the array takes **O(N log N)**, where `N` is the number of strings.
* Finding the common prefix between the first and last string takes **O(M)**, where `M` is the length of the shortest string.

**Overall Complexity:**

$$
O(N \log N + M)
$$

---

## Space Complexity

* Sorting uses extra space depending on the sorting algorithm (`O(1)` for in-place or `O(N)` otherwise).
* Other than that, only a few variables are used → **O(1)**.

```

---

Do you want me to also give you the **.md file ready to download** (instead of just the text), so you can directly use it?
```
