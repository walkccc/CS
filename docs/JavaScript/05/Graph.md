```js
class Graph {
  constructor() {
    this.adjList = {};
  }

  addVertex(vertex) {
    if (!this.adjList[vertex]) this.adjList[vertex] = [];
  }

  addEdge(v1, v2) {
    this.adjList[v1] = [...this.adjList[v1], v2];
    this.adjList[v2] = [...this.adjList[v2], v1];
  }

  removeEdge(v1, v2) {
    this.adjList[v1] = this.adjList[v1].filter(v => v !== v2);
    this.adjList[v2] = this.adjList[v2].filter(v => v !== v1);
  }

  removeVertex(vertex) {
    while (this.adjList[vertex].length) {
      const adjVertex = this.adjList[vertex].pop();
      this.removeEdge(vertex, adjVertex);
    }
    delete this.adjList[vertex];
  }

  dfsRecursive(start) {
    const ret = [];
    const visited = {};
    const adjList = this.adjList;

    (function dfs(vertex) {
      if (!vertex) return null;

      visited[vertex] = true;
      ret.push(vertex);

      adjList[vertex].forEach(neighbor => {
        if (!visited[neighbor]) {
          return dfs(neighbor);
        }
      });
    })(start);

    return ret;
  }

  dfsIterative(start) {
    const ret = [];
    const visited = {};
    const stack = [start];
    let currVertex;

    visited[start] = true;

    while (stack.length) {
      currVertex = stack.pop();
      ret.push(currVertex);

      this.adjList[currVertex].forEach(neighbor => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          stack.push(neighbor);
        }
      });
    }

    return ret;
  }

  bfs(start) {
    const ret = [];
    const visited = {};
    const queue = [start];
    let currVertex;

    visited[start] = true;

    while (queue.length) {
      currVertex = queue.shift();
      ret.push(currVertex);

      this.adjList[currVertex].forEach(neighbor => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          queue.push(neighbor);
        }
      });
    }

    return ret;
  }
}
```

```js
let g = new Graph();

g.addVertex('A');
g.addVertex('B');
g.addVertex('C');
g.addVertex('D');
g.addVertex('E');
g.addVertex('F');

g.addEdge('A', 'B');
g.addEdge('A', 'C');
g.addEdge('B', 'D');
g.addEdge('C', 'E');
g.addEdge('D', 'E');
g.addEdge('D', 'F');
g.addEdge('E', 'F');

//    A
//  /   \
// B     C
// |     |
// D  -  E
//  \   /
//    F

g.dfsRecursive('A'); // ['A', 'B', 'D', 'E', 'C', 'F']
g.dfsIterative('A'); // ['A', 'C', 'E', 'F', 'D', 'B']
g.bfs('A'); // ['A', 'B', 'C', 'D', 'E', 'F']
```
