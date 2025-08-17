### 🏔️ What is a Mountain Array?

A **mountain array** is defined as:

* An array where:

  * Elements strictly **increase to a peak**, and then
  * Strictly **decrease** after the peak.
* It has **at least 3 elements**, like:

  ```cpp
  [1, 3, 5, 6, 4, 2]
              ↑
           (peak)
  ```

---
### 🏔️ **Java Code – Find Peak Index in a Mountain Array**

```java
import java.util.*;
public class Main{
    public static int peak(int[] arr){
        int st=1;
        int end=arr.length-1;
        while(st<end){
            int mid=st+(end-st)/2;
            if(arr[mid-1]<arr[mid] && arr[mid]>arr[mid+1]){
                return mid;
            }
            else if(arr[mid-1]<arr[mid]){
                st=mid+1;
            }
            else{
                end=mid-1;
            }
        }
        return -1;
    }
    public static void main(String args[]){
        int[] el={0, 3, 8, 9, 5, 2};
        int element=peak(el);
        System.out.println(element);
    }
}
```

---

### ✅ Output

```
Peak index: 3
```

---

### ⏱️ **Time & Space Complexity**

* **Time:** `O(log n)` – Binary Search
* **Space:** `O(1)` – Constant extra space

---

If you want, I can also give you a **Java version that directly returns the peak value** instead of the index, depending on what your problem statement requires.
