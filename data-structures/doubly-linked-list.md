# Doubly Linked List

The only difference between a linked list and a doubly linked list is that you can traverse in either direction in doubly linked list, which is helpful in certain scenarios \( for example implementing LRU cache\).

You can create a **Node Class** having previous, next and value as data members.

```javascript
class Node {

    constructor(val) {
        this.val = val;
        this.next = null;
        this.prev = null;
    }
}
```

And then create a **Doubly Linked List Class** for any sort of operations you want to perform.

```javascript
class Node {

    constructor(val) {
        this.val = val;
        this.next = null;
        this.prev = null;
    }
}

class DoublyLinkedList {

    addNode(node, val) {
        const newNode = new Node(val);
        newNode.prev = node;
        node.next = newNode;

        return newNode;
    }

    travserse(head) {
        let currentNode = head;

        while (currentNode !== null) {
            console.log(currentNode.val);
            currentNode = currentNode.next;
        }
    }
}
```

