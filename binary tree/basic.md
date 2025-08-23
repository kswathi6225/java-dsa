
## **Binary Tree Java Example – Full Code**

```java
// Node class
class Node {
    int data;
    Node left;
    Node right;

    Node(int data) {
        this.data = data;
        this.left = null;
        this.right = null;
    }
}

// Binary Tree class
class BinaryTree {
    Node root;

    BinaryTree() {
        root = null;
    }

    // Preorder Traversal (Root → Left → Right)
    void preorder(Node node) {
        if (node == null) return;
        System.out.print(node.data + " ");
        preorder(node.left);
        preorder(node.right);
    }

    // Inorder Traversal (Left → Root → Right)
    void inorder(Node node) {
        if (node == null) return;
        inorder(node.left);
        System.out.print(node.data + " ");
        inorder(node.right);
    }

    // Postorder Traversal (Left → Right → Root)
    void postorder(Node node) {
        if (node == null) return;
        postorder(node.left);
        postorder(node.right);
        System.out.print(node.data + " ");
    }

    // Height of Binary Tree
    int height(Node node) {
        if (node == null) return 0;
        int leftHeight = height(node.left);
        int rightHeight = height(node.right);
        return Math.max(leftHeight, rightHeight) + 1;
    }

    // Count total nodes
    int countNodes(Node node) {
        if (node == null) return 0;
        return 1 + countNodes(node.left) + countNodes(node.right);
    }
}

// Main class
public class Main {
    public static void main(String[] args) {
        BinaryTree tree = new BinaryTree();

        // Creating tree
        tree.root = new Node(1);
        tree.root.left = new Node(2);
        tree.root.right = new Node(3);
        tree.root.left.left = new Node(4);
        tree.root.left.right = new Node(5);

        // Traversals
        System.out.print("Preorder: ");
        tree.preorder(tree.root);
        System.out.println();

        System.out.print("Inorder: ");
        tree.inorder(tree.root);
        System.out.println();

        System.out.print("Postorder: ");
        tree.postorder(tree.root);
        System.out.println();

        // Height
        System.out.println("Height of tree: " + tree.height(tree.root));

        // Count nodes
        System.out.println("Total nodes: " + tree.countNodes(tree.root));
    }
}
```

---

### ✅ **Output**

```
Preorder: 1 2 4 5 3 
Inorder: 4 2 5 1 3 
Postorder: 4 5 2 3 1 
Height of tree: 3
Total nodes: 5
```

---

### **Explanation**

1. `Node` class → stores **data, left, right**.
2. `BinaryTree` → has methods for **traversals, height, and node count**.
3. **Traversal** methods are **recursive**.
4. **Height** → max depth from root to leaf.
5. **CountNodes** → counts all nodes recursively.

---

If you want, I can now **teach you level order traversal (BFS) and simple binary tree problems like "find sum, max value, leaf nodes"** so you can **start solving interview problems**.

Do you want me to go there next?
