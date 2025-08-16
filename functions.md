## 🔹 **Common StringBuilder Methods**

### 1. **append()**

Adds text at the end.

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb); // Hello World
```

---

### 2. **insert(int offset, String str)**

Inserts text at a given index.

```java
StringBuilder sb = new StringBuilder("HelloWorld");
sb.insert(5, " Java");
System.out.println(sb); // Hello JavaWorld
```

---

### 3. **delete(int start, int end)**

Deletes characters from `start` to `end-1`.

```java
StringBuilder sb = new StringBuilder("HelloWorld");
sb.delete(5, 7); 
System.out.println(sb); // Hellorld
```

---

### 4. **deleteCharAt(int index)**

Deletes a single character.

```java
StringBuilder sb = new StringBuilder("Hello");
sb.deleteCharAt(1); 
System.out.println(sb); // Hllo
```

---

### 5. **replace(int start, int end, String str)**

Replaces characters from `start` to `end-1` with new text.

```java
StringBuilder sb = new StringBuilder("HelloWorld");
sb.replace(5, 10, "Java");
System.out.println(sb); // HelloJava
```

---

### 6. **reverse()**

Reverses the whole string.

```java
StringBuilder sb = new StringBuilder("Hello");
sb.reverse();
System.out.println(sb); // olleH
```

---

### 7. **capacity()**

Shows current buffer capacity (not length).

```java
StringBuilder sb = new StringBuilder("Hello");
System.out.println(sb.capacity()); // default 16 + length of string
```

---

### 8. **ensureCapacity(int minCapacity)**

Ensures minimum buffer size.

```java
StringBuilder sb = new StringBuilder();
sb.ensureCapacity(50); 
System.out.println(sb.capacity()); // >= 50
```

---

### 9. **charAt(int index)**

Returns a character at given position.

```java
StringBuilder sb = new StringBuilder("Hello");
System.out.println(sb.charAt(1)); // e
```

---

### 10. **setCharAt(int index, char ch)**

Replaces a single character.

```java
StringBuilder sb = new StringBuilder("Hello");
sb.setCharAt(1, 'a');
System.out.println(sb); // Hallo
```

---

### 11. **length()**

Returns number of characters.

```java
StringBuilder sb = new StringBuilder("Hello");
System.out.println(sb.length()); // 5
```

---

### 12. **substring(int start) / substring(int start, int end)**

Extracts part of the string.

```java
StringBuilder sb = new StringBuilder("HelloWorld");
System.out.println(sb.substring(5));     // World
System.out.println(sb.substring(0, 5));  // Hello
```


## **1. List Interface (e.g., `ArrayList`, `LinkedList`)**

* Maintains insertion order
* Allows duplicate elements
* Index-based access

**Common Methods:**

```java
add(E e)                  // Add element to end
add(int index, E e)       // Insert at specific index
get(int index)            // Get element at index
set(int index, E e)       // Replace element at index
remove(int index)         // Remove element at index
remove(Object o)          // Remove first occurrence of object
size()                    // Number of elements
contains(Object o)        // Check if exists
isEmpty()                 // Check if empty
indexOf(Object o)         // First occurrence index
lastIndexOf(Object o)     // Last occurrence index
clear()                   // Remove all elements
subList(int from, int to) // Portion of list
```

---

## **2. Set Interface (e.g., `HashSet`, `LinkedHashSet`, `TreeSet`)**

* No duplicate elements
* No guaranteed order (except `LinkedHashSet` and sorted order in `TreeSet`)

**Common Methods:**

```java
add(E e)                 // Add element
remove(Object o)         // Remove element
contains(Object o)       // Check existence
size()                   // Number of elements
isEmpty()                // Check if empty
clear()                  // Remove all elements
addAll(Collection c)     // Union
retainAll(Collection c)  // Intersection
removeAll(Collection c)  // Difference
toArray()                // Convert to array
```

---

## **3. Map Interface (e.g., `HashMap`, `LinkedHashMap`, `TreeMap`)**

* Stores **key-value pairs**
* Keys are unique, values can be duplicated

**Common Methods:**

```java
put(K key, V value)                 // Add key-value
putAll(Map m)                       // Add all from another map
get(Object key)                     // Get value by key
remove(Object key)                  // Remove key-value by key
containsKey(Object key)             // Check if key exists
containsValue(Object value)         // Check if value exists
size()                              // Number of entries
isEmpty()                           // Check if empty
clear()                             // Remove all entries
keySet()                            // Get all keys
values()                            // Get all values
entrySet()                          // Get all key-value pairs
replace(K key, V value)             // Replace value for key
replace(K key, V oldVal, V newVal)  // Replace only if matches old value
getOrDefault(Object key, V default) // Get value or default if absent
```

---

If you want, I can also give **one Java program** that demonstrates **all these functions** in **`List`, `Set`, and `Map`** in a single file so you can run and revise.
That way you don’t just read them—you’ll see the output for each.

Do you want me to prepare that?
