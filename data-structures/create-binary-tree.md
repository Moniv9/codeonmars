# Create a Binary Tree

In binary tree **parent node** have at most 2 child nodes. And node can store either a number, string or an object.

```javascript
class Node {

    constructor(val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

class BinaryTree {

    addRootNode(val) {
        return new Node(val);
    }

    addLeftNode(node, val) {
        const newNode = new Node(val);
        node.left = newNode;

        return newNode;
    }

    addRightNode(node, val) {
        const newNode = new Node(val);
        node.right = newNode;

        return newNode;
    }
}
```



Using instance of binary tree class to create root and child nodes.

```javascript
const binaryTree = new BinaryTree();
const root = binaryTree.addRootNode(1);

const leftNode = binaryTree.addLeftNode(root, 2);
const rightNode = binaryTree.addRightNode(root, 3);

binaryTree.addLeftNode(leftNode, 4);
binaryTree.addRightNode(leftNode, 5);
```



Binary tree can be traversed in 3 orders.

> In order = Left Node, Root Node and Right Node
>
> Pre Order = Root Node, Left Node and Right Node
>
> Post Order = Left Node, Right Node and Root Node



```javascript
class Node {

    constructor(val) {
        this.val = val;
        this.left = null;
        this.right = null;
    }
}

class BinaryTree {

    addRootNode(val) {
        return new Node(val);
    }

    addLeftNode(node, val) {
        const newNode = new Node(val);
        node.left = newNode;

        return newNode;
    }

    addRightNode(node, val) {
        const newNode = new Node(val);
        node.right = newNode;

        return newNode;
    }

    inorderTraverse(root) {
        if (root === null) {
            return;
        }

        this.inorderTraverse(root.left);
        console.log(root.val);
        this.inorderTraverse(root.right);
    }

    preorderTraversal(root) {
        if (root === null) {
            return;
        }

        console.log(root.val);
        this.preorderTraversal(root.left);
        this.inorderTraverse(root.right);
    }

    postorderTraversal(root) {
        if (root === null) {
            return;
        }

        this.preorderTraversal(root.left);
        this.inorderTraverse(root.right);
        console.log(root.val);
    }
}
```

