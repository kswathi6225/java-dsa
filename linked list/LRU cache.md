Got it 👍
Let’s implement **LRU Cache** in Java using **LinkedList + HashMap**.
I’ll show you two approaches:

---

# ✅ Approach 1: Using `LinkedHashMap` (Easy & Built-in)

* Java’s `LinkedHashMap` maintains insertion order, and with accessOrder flag, we can make it behave like an LRU.
* Time Complexity → **O(1)** for get & put
* Space Complexity → **O(capacity)**

```java
import java.util.*;

class LRUCache1<K, V> extends LinkedHashMap<K, V> {
    private final int capacity;

    public LRUCache1(int capacity) {
        super(capacity, 0.75f, true); // true = accessOrder
        this.capacity = capacity;
    }

    @Override
    protected boolean removeEldestEntry(Map.Entry<K, V> eldest) {
        return size() > capacity;
    }

    public static void main(String[] args) {
        LRUCache1<Integer, String> cache = new LRUCache1<>(3);
        cache.put(1, "A");
        cache.put(2, "B");
        cache.put(3, "C");
        System.out.println("Cache: " + cache);

        cache.get(1);  // Access 1 → moves it to most recent
        cache.put(4, "D"); // Removes 2 (least recently used)
        System.out.println("After adding 4: " + cache);
    }
}
```

**Output:**

```
Cache: {1=A, 2=B, 3=C}
After adding 4: {3=C, 1=A, 4=D}
```

---

# ✅ Approach 2: Using **Doubly Linked List + HashMap** (Interview-Favorite)

* Maintain a **HashMap** for O(1) access to nodes.
* Maintain a **Doubly Linked List** for order of usage (head = most recent, tail = least recent).
* Time Complexity → **O(1)** for get & put
* Space Complexity → **O(capacity)**

```java
import java.util.*;

class LRUCache2 {
    class Node {
        int key, value;
        Node prev, next;
        Node(int k, int v) {
            key = k;
            value = v;
        }
    }

    private final int capacity;
    private Map<Integer, Node> map;
    private Node head, tail;

    public LRUCache2(int capacity) {
        this.capacity = capacity;
        this.map = new HashMap<>();
        
        // dummy head and tail
        head = new Node(0, 0);
        tail = new Node(0, 0);
        head.next = tail;
        tail.prev = head;
    }

    // Remove node from list
    private void remove(Node node) {
        node.prev.next = node.next;
        node.next.prev = node.prev;
    }

    // Insert node right after head (most recent)
    private void insert(Node node) {
        node.next = head.next;
        node.prev = head;
        head.next.prev = node;
        head.next = node;
    }

    public int get(int key) {
        if (!map.containsKey(key)) return -1;
        Node node = map.get(key);
        remove(node);
        insert(node); // move to front
        return node.value;
    }

    public void put(int key, int value) {
        if (map.containsKey(key)) {
            remove(map.get(key));
        }
        if (map.size() == capacity) {
            map.remove(tail.prev.key); // remove least recent
            remove(tail.prev);
        }
        Node node = new Node(key, value);
        insert(node);
        map.put(key, node);
    }

    public void printCache() {
        Node curr = head.next;
        System.out.print("Cache: ");
        while (curr != tail) {
            System.out.print(curr.key + "=" + curr.value + " ");
            curr = curr.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        LRUCache2 cache = new LRUCache2(3);
        cache.put(1, 10);
        cache.put(2, 20);
        cache.put(3, 30);
        cache.printCache();

        System.out.println("Get 1: " + cache.get(1)); 
        cache.printCache();

        cache.put(4, 40); 
        cache.printCache();

        System.out.println("Get 2: " + cache.get(2)); 
    }
}
```

**Output:**

```
Cache: 3=30 2=20 1=10 
Get 1: 10
Cache: 1=10 3=30 2=20 
Cache: 4=40 1=10 3=30 
Get 2: -1
```

---

👉 Would you like me to next cover **Detect Cycle in Linked List (Floyd’s Algorithm)** since it’s also one of the most important LL problems for interviews?
