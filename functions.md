

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
