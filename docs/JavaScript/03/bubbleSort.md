# Bubble Sort

## `swap(arr, i, j)`

```js
const swap = (arr, i, j) => {
  [arr[i], arr[j]] = [arr[j], arr[i]];
};
```

## `bubbleSort(arr)`

```js
const bubbleSort = arr => {
  for (let i = arr.length - 1; i > 0; i--) {
    let noSwaps = true;

    for (let j = 0; j < i; j++) {
      if (arr[j] > arr[j + 1]) {
        swap(arr, j, j + 1);
        noSwaps = false;
      }
    }

    if (noSwaps) break;
  }

  return arr;
};
```
