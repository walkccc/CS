```js
class Node {
  constructor(val) {
    this.val = val;
    this.left = null;
    this.right = null;
  }
}
```

```js
class BinarySearchTree {
  constructor() {
    this.root = null;
  }

  insert(val) {
    const newNode = new Node(val);

    if (this.root === null) {
      this.root = newNode;
      return this;
    }

    let curr = this.root;

    while (true) {
      if (val === curr.val) return undefined;
      if (val < curr.val) {
        if (curr.left === null) {
          curr.left = newNode;
          return this;
        }
        curr = curr.left;
      } else {
        if (curr.right === null) {
          curr.right = newNode;
          return this;
        }
        curr = curr.right;
      }
    }
  }

  find(val) {
    if (this.root === null) return false;

    let curr = this.root;
    let found = false;

    while (curr && !found) {
      if (val < curr.val) {
        curr = curr.left;
      } else if (val > curr.val) {
        curr = curr.right;
      } else {
        found = true;
      }
    }

    if (!found) return undefined;
    return curr;
  }

  contains(val) {
    if (this.root === null) return false;

    let curr = this.root;
    let found = false;

    while (curr && !found) {
      if (val < curr.val) {
        curr = curr.left;
      } else if (val > curr.val) {
        curr = curr.right;
      } else {
        return true;
      }
    }

    return false;
  }

  bfs() {
    let node = this.root;
    const ret = [];
    const queue = [node];

    while (queue.length) {
      node = queue.shift();
      ret.push(node.val);
      if (node.left) queue.push(node.left);
      if (node.right) queue.push(node.right);
    }

    return ret;
  }

  dfs() {
    let node = this.root;
    const ret = [];
    const stack = [node];

    while (stack.length) {
      node = stack.pop();
      ret.push(node.val);
      if (node.right) stack.push(node.right);
      if (node.left) stack.push(node.left);
    }

    return ret;
  }

  preOrder() {
    const ret = [];

    const traverse = node => {
      ret.push(node.val);
      if (node.left) traverse(node.left);
      if (node.right) traverse(node.right);
    };

    traverse(this.root);

    return ret;
  }

  postOrder() {
    const ret = [];

    const traverse = node => {
      if (node.left) traverse(node.left);
      if (node.right) traverse(node.right);
      ret.push(node.val);
    };

    traverse(this.root);

    return ret;
  }

  inOrder() {
    const ret = [];

    const traverse = node => {
      if (node.left) traverse(node.left);
      ret.push(node.val);
      if (node.right) traverse(node.right);
    };

    traverse(this.root);

    return ret;
  }
}
```

```js
var tree = new BinarySearchTree();

tree.insert(10);
tree.insert(6);
tree.insert(3);
tree.insert(8);
tree.insert(15);
tree.insert(20);

//     10
//   6    15
// 3  8     20

tree.bfs(); // [10, 6, 15, 3, 8, 20]
tree.dfs(); // [10, 6, 3, 8, 15, 20]
tree.preOrder(); // [10, 6, 3, 8, 15, 20]
tree.postOrder(); // [3, 8, 6, 20, 15, 10]
tree.inOrder(); // [3, 6, 8, 10, 15, 20]
```
