```js
class Node {
  constructor(val, priority) {
    this.val = val;
    this.priority = priority;
  }
}
```

```js
class MaxPriorityQueue {
  constructor() {
    this.arr = [];
  }

  enqueue(val, priority) {
    const newNode = new Node(val, priority);
    this.arr = [...this.arr, newNode];
    this.bubbleUp();
  }

  bubbleUp() {
    let index = this.arr.length - 1;
    const elem = this.arr[index];

    while (index > 0) {
      let parentIndex = Math.floor((index - 1) / 2);
      let parent = this.arr[parentIndex];

      if (elem.priority <= parent.priority) break;

      this.arr[parentIndex] = elem;
      this.arr[index] = parent;
      index = parentIndex;
    }
  }

  dequeue() {
    const max = this.arr[0];
    const end = this.arr.pop();

    if (this.arr.length > 0) {
      this.arr[0] = end;
      this.sinkDown();
    }

    return max;
  }

  sinkDown() {
    let index = 0;
    const { length } = this.arr;
    const elem = this.arr[index];

    while (true) {
      let leftChildIndex = 2 * index + 1;
      let rightChildIndex = 2 * index + 2;
      let leftChild = null;
      let rightChild = null;
      let swap = null;

      if (leftChildIndex < length) {
        leftChild = this.arr[leftChildIndex];
        if (leftChild.priority > elem.priority) {
          swap = leftChildIndex;
        }
      }

      if (rightChildIndex < length) {
        rightChild = this.arr[rightChildIndex];
        if (
          (swap === null && rightChild.priority > elem.priority) ||
          (swap !== null && rightChild.priority > leftChild.priority)
        ) {
          swap = rightChildIndex;
        }
      }

      if (swap === null) break;

      this.arr[index] = this.arr[swap];
      this.arr[swap] = elem;
      index = swap;
    }
  }
}
```

```js
let queue = new MaxPriorityQueue();

queue.enqueue('Drink water', 1);
queue.enqueue('Sleep', 5);
queue.enqueue('Eat', 2);
```
