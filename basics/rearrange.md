```java
import java.util.*;

public class Main {

    // 1. Rearrange positive and negative numbers alternately
    public static int[] rearrangePosNeg(int[] arr) {
        List<Integer> pos = new ArrayList<>();
        List<Integer> neg = new ArrayList<>();

        for (int num : arr) {
            if (num >= 0) pos.add(num);
            else neg.add(num);
        }

        int i = 0, j = 0;
        List<Integer> result = new ArrayList<>();

        while (i < neg.size() && j < pos.size()) {
            result.add(neg.get(i++));
            result.add(pos.get(j++));
        }
        while (i < neg.size()) result.add(neg.get(i++));
        while (j < pos.size()) result.add(pos.get(j++));

        // Convert List to array
        int[] resArr = new int[result.size()];
        for (int k = 0; k < result.size(); k++) resArr[k] = result.get(k);
        return resArr;
    }

    // 2. Convert [1, 2, 3, 4, 5] -> [1, 5, 2, 4, 3]
    public static int[] rearrangeSequence(int[] arr) {
        int n = arr.length;
        int[] result = new int[n];
        int left = 0, right = n - 1;
        int idx = 0;

        while (left <= right) {
            if (left == right) {
                result[idx++] = arr[left];
            } else {
                result[idx++] = arr[left++];
                result[idx++] = arr[right--];
            }
        }
        return result;
    }

    // Driver code
    public static void main(String[] args) {
        int[] arr1 = {-5, 5, -2, 2, -8, 4, 7, 1, 8, 0};
        System.out.println("Rearranged Pos-Neg: " + Arrays.toString(rearrangePosNeg(arr1)));

        int[] arr2 = {1, 2, 3, 4, 5};
        System.out.println("Rearranged Sequence: " + Arrays.toString(rearrangeSequence(arr2)));
    }
}
```

---

