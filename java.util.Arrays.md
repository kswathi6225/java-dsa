## 🔹 Common Inbuilt Functions on Arrays in Java

### 1. **Sorting**

* **Ascending order:**

  ```java
  import java.util.Arrays;
  int[] arr = {5, 2, 9, 1, 6};
  Arrays.sort(arr);
  System.out.println(Arrays.toString(arr)); // [1, 2, 5, 6, 9]
  ```

* **Sorting part of array:**

  ```java
  Arrays.sort(arr, 1, 4); // sorts from index 1 to 3
  ```

---

### 2. **Searching**

* **Binary Search (only works on sorted arrays):**

  ```java
  int index = Arrays.binarySearch(arr, 6);
  System.out.println(index); // prints index of 6
  ```

---

### 3. **Comparisons**

* **Equals check:**

  ```java
  int[] arr1 = {1, 2, 3};
  int[] arr2 = {1, 2, 3};
  System.out.println(Arrays.equals(arr1, arr2)); // true
  ```

* **Deep equals (for multidimensional arrays):**

  ```java
  int[][] mat1 = {{1,2}, {3,4}};
  int[][] mat2 = {{1,2}, {3,4}};
  System.out.println(Arrays.deepEquals(mat1, mat2)); // true
  ```

---

### 4. **Fill Arrays**

* **Fill all values:**

  ```java
  int[] arr = new int[5];
  Arrays.fill(arr, 7);
  System.out.println(Arrays.toString(arr)); // [7, 7, 7, 7, 7]
  ```

* **Fill part of array:**

  ```java
  Arrays.fill(arr, 1, 4, 9); // fills index 1 to 3 with 9
  ```

---

### 5. **Copying Arrays**

* **Copy whole array:**

  ```java
  int[] copy = Arrays.copyOf(arr, 3);
  System.out.println(Arrays.toString(copy));
  ```

* **Copy range:**

  ```java
  int[] part = Arrays.copyOfRange(arr, 2, 5);
  ```

---

### 6. **Convert to String**

* **1D array:**

  ```java
  System.out.println(Arrays.toString(arr));
  ```

* **2D (or multi-D) array:**

  ```java
  int[][] mat = {{1,2}, {3,4}};
  System.out.println(Arrays.deepToString(mat)); // [[1, 2], [3, 4]]
  ```

---

### 7. **Parallel Sort (faster for big arrays)**

* Uses multiple threads internally.

  ```java
  Arrays.parallelSort(arr);
  ```

---

## 🔹 Situations to Use Arrays

* When **size is fixed** and known in advance.
* When you need **fast index-based access**.
* When working with **primitive types** (int, char, etc.) where ArrayList uses objects and consumes more memory.

---

👉 Meanwhile, **ArrayList** should be used when:

* You don’t know the size in advance.
* You need frequent insertions/deletions.
* You want built-in dynamic resizing and more utility methods.

---

Would you like me to also give you a **list of practice problems** (like reverse, rotate, max-min, prefix sum, etc.) you can solve to master arrays step by step?
