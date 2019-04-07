```js
class Node {
  constructor(val) {
    this.val = val;
    this.next = null;
  }
}
```

```js
class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }

  push(val) {
    const newNode = new Node(val);

    if (!this.head) {
      this.head = newNode;
      this.tail = this.head;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }

    this.length++;
    return this;
  }

  pop() {
    if (!this.head) return undefined;

    let poppedNode = this.head;
    let newTail = poppedNode;

    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    } else {
      while (poppedNode.next) {
        newTail = poppedNode;
        poppedNode = poppedNode.next;
      }
      this.tail = newTail;
      this.tail.next = null;
    }

    this.length--;
    return poppedNode;
  }

  shift() {
    if (this.length === 0) return undefined;

    let oldHead = this.head;

    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    } else {
      this.head = oldHead.next;
      oldHead.next = null;
    }

    this.length--;
    return oldHead;
  }

  unshift(val) {
    const newNode = new Node(val);

    if (this.length === 0) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      newNode.next = this.head;
      this.head = newNode;
    }

    this.length++;
    return this;
  }

  get(index) {
    if (index < 0 || index >= this.length) return null;

    let count = 0;
    let curr = this.head;

    while (count !== index) {
      curr = curr.next;
      count++;
    }

    return curr;
  }

  set(index, val) {
    let foundNode = this.get(index);

    if (foundNode) {
      foundNode.val = val;
      return true;
    }

    return false;
  }

  insert(index, val) {
    if (index < 0 || index > this.length) return false;
    if (index === 0) return this.unshift(val);
    if (index === this.length) return [...this, val];

    const newNode = new Node(val);
    let prev = this.get(index - 1);
    let next = prev.next;

    prev.next = newNode;
    newNode.next = next;

    this.length++;
    return true;
  }

  remove(index) {
    if (index < 0 || index >= this.length) return undefined;
    if (index === 0) return this.shift();
    if (index === this.length - 1) return this.pop();

    let prev = this.get(index - 1);
    let removedNode = prev.next;

    prev.next = removedNode.next;
    removedNode.next = null;

    this.length--;
    return removedNode;
  }

  reverse() {
    let node = this.head;
    this.head = this.tail;
    this.tail = node;

    let oldNext;
    let prev = null;

    for (let i = 0; i < this.length; i++) {
      oldNext = node.next;
      node.next = prev;
      prev = node;
      node = oldNext;
    }

    return this;
  }

  print() {
    const arr = [];
    let curr = this.head;

    while (curr) {
      arr.push(curr.val);
      curr = curr.next;
    }

    console.log(arr);
  }
}
```

```js
let list = new SinglyLinkedList();

for (let i = 0; i < 5; i++) list.push(i);
```
