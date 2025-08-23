Awesome! Let’s start **step by step**. We’ll begin with **all the basic Binary Tree operations in Java**, fully coded with **dry-run explanations**.

---

# **Step 1: Basic Binary Tree Operations**

We’ll cover:

1. Create a tree
2. Traversals: Preorder, Inorder, Postorder, Level Order
3. Height of tree
4. Count total nodes
5. Count leaf nodes
6. Maximum value
7. Sum of all nodes

---

## **Java Code: Complete Basics**

```java
import java.util.*;

// Node class
class Node {
    int data;
    Node left, right;

    Node(int data) {
        this.data = data;
        left = right = null;
    }
}

// Binary Tree class
class BinaryTree {
    Node root;

    BinaryTree() {
        root = null;
    }

    // 1️⃣ Preorder Traversal (Root → Left → Right)
    void preorder(Node node) {
        if (node == null) return;
        System.out.print(node.data + " ");
        preorder(node.left);
        preorder(node.right);
    }

    // 2️⃣ Inorder Traversal (Left → Root → Right)
    void inorder(Node node) {
        if (node == null) return;
        inorder(node.left);
        System.out.print(node.data + " ");
        inorder(node.right);
    }

    // 3️⃣ Postorder Traversal (Left → Right → Root)
    void postorder(Node node) {
        if (node == null) return;
        postorder(node.left);
        postorder(node.right);
        System.out.print(node.data + " ");
    }

    // 4️⃣ Level Order Traversal (BFS)
    void levelOrder() {
        if (root == null) return;
        Queue<Node> q = new LinkedList<>();
        q.add(root);

        while (!q.isEmpty()) {
            Node curr = q.poll();
            System.out.print(curr.data + " ");
            if (curr.left != null) q.add(curr.left);
            if (curr.right != null) q.add(curr.right);
        }
    }

    // 5️⃣ Height of Tree
    int height(Node node) {
        if (node == null) return 0;
        return Math.max(height(node.left), height(node.right)) + 1;
    }

    // 6️⃣ Count total nodes
    int countNodes(Node node) {
        if (node == null) return 0;
        return 1 + countNodes(node.left) + countNodes(node.right);
    }

    // 7️⃣ Count leaf nodes
    int countLeafNodes(Node node) {
        if (node == null) return 0;
        if (node.left == null && node.right == null) return 1;
        return countLeafNodes(node.left) + countLeafNodes(node.right);
    }

    // 8️⃣ Maximum value in tree
    int maxValue(Node node) {
        if (node == null) return Integer.MIN_VALUE;
        return Math.max(node.data, Math.max(maxValue(node.left), maxValue(node.right)));
    }

    // 9️⃣ Sum of all nodes
    int sumNodes(Node node) {
        if (node == null) return 0;
        return node.data + sumNodes(node.left) + sumNodes(node.right);
    }
}

// Main class
public class Main {
    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        // Create tree
        tree.root = new Node(1);
        tree.root.left = new Node(2);
        tree.root.right = new Node(3);
        tree.root.left.left = new Node(4);
        tree.root.left.right = new Node(5);

        System.out.print("Preorder: ");
        tree.preorder(tree.root);
        System.out.println();

        System.out.print("Inorder: ");
        tree.inorder(tree.root);
        System.out.println();

        System.out.print("Postorder: ");
        tree.postorder(tree.root);
        System.out.println();

        System.out.print("Level Order: ");
        tree.levelOrder();
        System.out.println();

        System.out.println("Height: " + tree.height(tree.root));
        System.out.println("Total Nodes: " + tree.countNodes(tree.root));
        System.out.println("Leaf Nodes: " + tree.countLeafNodes(tree.root));
        System.out.println("Maximum Value: " + tree.maxValue(tree.root));
        System.out.println("Sum of all Nodes: " + tree.sumNodes(tree.root));
    }
}
```

---

## **Dry Run & Output**

**Tree Structure:**

```
       1
     /   \
    2     3
   / \
  4   5
```

**Traversals:**

* Preorder → `1 2 4 5 3`
* Inorder → `4 2 5 1 3`
* Postorder → `4 5 2 3 1`
* Level Order → `1 2 3 4 5`

**Other Results:**

* Height → 3
* Total nodes → 5
* Leaf nodes → 3 (nodes 4, 5, 3)
* Maximum value → 5
* Sum of all nodes → 15

---

Swathi, once you **practice this code** and **dry run**, we can move to **Intermediate problems** like:

1. **Diameter of tree**
2. **Lowest Common Ancestor**
3. **Balanced Tree Check**
4. **Mirror Tree**

This will slowly move you to **interview-level questions**.

Do you want me to **start with Diameter of Binary Tree next**?
