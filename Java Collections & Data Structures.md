
---

# 📝 Java Collections & Data Structures – Quick Notes

---

## 🔹 1. **Array**

* Fixed-size, ordered collection of elements of same type.
* **Syntax**: `int[] arr = {1, 2, 3, 4};`

✅ Properties:

* Indexed (0-based).
* Fixed length (cannot resize).
* Allows duplicates.
* Stores homogeneous data.

⏱️ Complexity:

* Access by index: O(1)
* Search: O(n)
* Insert/Delete: O(n)

---

## 🔹 2. **ArrayList** (like Python List)

* Resizable array (part of `java.util`).
* **Syntax**:

  ```java
  ArrayList<Integer> list = new ArrayList<>();
  list.add(10);
  list.add(20);
  ```

✅ Properties:

* Ordered, indexed.
* Allows duplicates.
* Dynamic size.

⏱️ Complexity:

* Access by index: O(1)
* Search: O(n)
* Insert/Delete (end): O(1) amortized
* Insert/Delete (middle): O(n)

---

## 🔹 3. **LinkedList**

* Doubly linked list implementation.
* **Syntax**:

  ```java
  LinkedList<Integer> list = new LinkedList<>();
  list.add(10);
  list.add(20);
  ```

✅ Properties:

* Ordered, but accessed sequentially.
* Allows duplicates.
* Good for frequent insertions/deletions.

⏱️ Complexity:

* Access by index: O(n)
* Insert/Delete (at ends): O(1)
* Search: O(n)

---

## 🔹 4. **HashSet** (like Python Set)

* Stores unique elements, no order.
* **Syntax**:

  ```java
  HashSet<Integer> set = new HashSet<>();
  set.add(10);
  set.add(20);
  ```

✅ Properties:

* Unordered, unique elements.
* No duplicates allowed.
* Allows one `null`.

⏱️ Complexity:

* Insert/Delete/Lookup: O(1) average
* Iteration: O(n)

---

## 🔹 5. **LinkedHashSet**

* Like `HashSet`, but maintains **insertion order**.

✅ Properties:

* Unique elements.
* Maintains order of insertion.

⏱️ Complexity: Same as HashSet (O(1) average).

---

## 🔹 6. **TreeSet**

* Implements `NavigableSet` → elements stored in sorted order.
* **Syntax**:

  ```java
  TreeSet<Integer> set = new TreeSet<>();
  set.add(30);
  set.add(10);
  set.add(20);
  System.out.println(set);  // [10,20,30]
  ```

✅ Properties:

* Unique elements.
* Sorted (natural order or custom comparator).

⏱️ Complexity:

* Insert/Delete/Lookup: O(log n)

---

## 🔹 7. **HashMap** (like Python Dictionary)

* Key-value pairs, unordered.
* **Syntax**:

  ```java
  HashMap<String, Integer> map = new HashMap<>();
  map.put("a", 1);
  map.put("b", 2);
  ```

✅ Properties:

* Keys must be unique (values can duplicate).
* Keys must be immutable (String, Integer, etc.).
* Allows one `null` key, multiple `null` values.

⏱️ Complexity:

* Insert/Delete/Lookup: O(1) average
* Iteration: O(n)

---

## 🔹 8. **LinkedHashMap**

* Like `HashMap`, but maintains **insertion order**.

---

## 🔹 9. **TreeMap**

* Sorted map (keys sorted).

✅ Properties:

* Keys are unique & sorted.
* No `null` key allowed.

⏱️ Complexity:

* Insert/Delete/Lookup: O(log n)

---

## 🔹 10. **String**

* Immutable sequence of characters.
* Similar to Python string.

✅ Example:

```java
String s = "hello";
System.out.println(s.charAt(0));  // 'h'
System.out.println(s.toUpperCase());  // "HELLO"
```

---

# 📌 Comparison Table (Python vs Java)

| Feature    | Python            | Java Equivalent                                                         |
| ---------- | ----------------- | ----------------------------------------------------------------------- |
| **Array**  | list (dynamic)    | Array (fixed size)                                                      |
| **List**   | list              | ArrayList, LinkedList                                                   |
| **Tuple**  | tuple (immutable) | No direct equivalent (use `List.of(...)` for immutable list in Java 9+) |
| **Set**    | set               | HashSet, LinkedHashSet, TreeSet                                         |
| **Dict**   | dict              | HashMap, LinkedHashMap, TreeMap                                         |
| **String** | str (immutable)   | String (immutable)                                                      |

---

⚡ Rule of thumb:

* **ArrayList** ↔ Python list
* **HashSet** ↔ Python set
* **HashMap** ↔ Python dict
* **Tuple** has no direct Java equivalent, but you can use `record`, `Pair<K,V>`, or custom class.

---

👉 Do you want me to also make **short “cheat sheet code examples”** (side-by-side Python vs Java) for each of these, so you can revise quickly before interviews?
