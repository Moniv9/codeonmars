---
description: >-
  Given a stack, find minimum element from it at any given time in O(1) time
  complexity
---

# Min Stack

{% hint style="info" %}
We take 2 stacks. One as **main stack** for inserting new element and another as **min stack** for keeping track of the min element.
{% endhint %}

While inserting new element into the main stack, we compare it with the top value of min stack. If it is empty or less than the top of min stack, we insert into it.

Now if we want to get min element from the **main stack**, we just peek the top element of the **min stack**. And while removing element from the **main stack**, we also remove it from the **min stack** if it is present on top of the **min stack**.

In this way we can get min element in O\(1\) time complexity.

```javascript
class MinStack {

    constructor() {
        this.mainStack = [];
        this.minStack = [];
    }

    insert(val) {
        this.mainStack.push(val);

        const length = this.minStack.length - 1;
        if (this.minStack.length === 0 || this.minStack[length] >= val) {
            this.minStack.push(val);
        }
    }

    remove() {
        const value = this.mainStack.pop();

        const length = this.minStack.length - 1;
        if (value === this.minStack[length]) {
            this.minStack.pop();
        }
    }

    getMin() {
        const length = this.minStack.length - 1;

        if (length >= 0) {
            return this.minStack[length];
        }
    }
}
```



