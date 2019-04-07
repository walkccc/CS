# Selection Sort

## `swap(arr, i, j)`

```js
const swap = (arr, i, j) => {
  [arr[i], arr[j]] = [arr[j], arr[i]];
};
```

## `selectionSort(arr)`

```js
const selectionSort = arr => {
  for (let i = 0; i < arr.length; i++) {
    let smallest = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[smallest] > arr[j]) {
        smallest = j;
      }
    }
    if (i !== smallest) swap(arr, i, smallest);
  }
  return arr;
};
```
