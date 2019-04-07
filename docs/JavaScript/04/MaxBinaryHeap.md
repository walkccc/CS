```js
class MaxBinaryHeap {
  constructor() {
    this.arr = [];
  }

  insert(elem) {
    this.arr = [...this.arr, elem];
    this.bubbleUp();
  }

  bubbleUp() {
    let index = this.arr.length - 1;
    const elem = this.arr[index];

    while (index > 0) {
      let parentIndex = Math.floor((index - 1) / 2);
      let parent = this.arr[parentIndex];

      if (elem <= parent) break;

      this.arr[parentIndex] = elem;
      this.arr[index] = parent;
      index = parentIndex;
    }
  }

  extractMax() {
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
        if (leftChild > elem) {
          swap = leftChildIndex;
        }
      }

      if (rightChildIndex < length) {
        rightChild = this.arr[rightChildIndex];
        if (
          (swap === null && rightChild > elem) ||
          (swap !== null && rightChild > leftChild)
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
let heap = new MaxBinaryHeap();

heap.insert(41);
heap.insert(39);
heap.insert(33);
heap.insert(18);
heap.insert(27);
heap.insert(12);
heap.insert(55);
// [55, 39, 41, 18, 27, 12, 33]

heap.extractMax(); // [41, 39, 33, 18, 27, 12]
```
