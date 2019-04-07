```js
class Node {
  constructor(val, priority) {
    this.val = val;
    this.priority = priority;
  }
}
```

```js
class MinPriorityQueue {
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

      if (elem.priority >= parent.priority) break;

      this.arr[parentIndex] = elem;
      this.arr[index] = parent;
      index = parentIndex;
    }
  }

  dequeue() {
    const min = this.arr[0];
    const end = this.arr.pop();

    if (this.arr.length > 0) {
      this.arr[0] = end;
      this.sinkDown();
    }

    return min;
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
        if (leftChild.priority < elem.priority) {
          swap = leftChildIndex;
        }
      }

      if (rightChildIndex < length) {
        rightChild = this.arr[rightChildIndex];
        if (
          (swap === null && rightChild.priority < elem.priority) ||
          (swap !== null && rightChild.priority < leftChild.priority)
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
class WeightedGraph {
  constructor() {
    this.adjList = {};
  }

  addVertex(vertex) {
    if (!this.adjList[vertex]) this.adjList[vertex] = [];
  }

  addEdge(v1, v2, weight) {
    this.adjList[v1] = [...this.adjList[v1], { node: v2, weight }];
    this.adjList[v2] = [...this.adjList[v2], { node: v1, weight }];
  }

  Dijkstra(start, end) {
    const nodes = new MinPriorityQueue();
    const dist = {};
    const prev = {};
    let path = [];
    let smallest;

    for (let vertex in this.adjList) {
      if (vertex === start) {
        dist[vertex] = 0;
        nodes.enqueue(vertex, 0);
      } else {
        dist[vertex] = Infinity;
        nodes.enqueue(vertex, Infinity);
      }
      prev[vertex] = null;
    }

    while (nodes.arr.length) {
      smallest = nodes.dequeue().val;
      if (smallest === end) {
        while (prev[smallest]) {
          path.push(smallest);
          smallest = prev[smallest];
        }
        break;
      }

      if (smallest || dist[smallest] !== Infinity) {
        for (let neighbor in this.adjList[smallest]) {
          let nextNode = this.adjList[smallest][neighbor];
          let candidate = dist[smallest] + nextNode.weight;
          let nextNeighbor = nextNode.node;

          if (candidate < dist[nextNeighbor]) {
            dist[nextNeighbor] = candidate;
            prev[nextNeighbor] = smallest;
            nodes.enqueue(nextNeighbor, candidate);
          }
        }
      }
    }

    return path.concat(smallest).reverse();
  }
}
```

```js
let g = new WeightedGraph();

g.addVertex('A');
g.addVertex('B');
g.addVertex('C');
g.addVertex('D');
g.addVertex('E');
g.addVertex('F');

g.addEdge('A', 'B', 4);
g.addEdge('A', 'C', 2);
g.addEdge('B', 'E', 3);
g.addEdge('C', 'D', 2);
g.addEdge('C', 'F', 4);
g.addEdge('D', 'E', 3);
g.addEdge('D', 'F', 1);
g.addEdge('E', 'F', 1);

g.Dijkstra('A', 'E'); // ['A', 'C', 'D', 'F', 'E']
```
