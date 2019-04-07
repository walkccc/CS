# Quick Sort

## `pivot(arr, left = 0, right = arr.length - 1)`

```js
const pivot = (arr, left, right) => {
  const swap = (arr, i, j) => {
    [arr[i], arr[j]] = [arr[j], arr[i]];
  };

  let pivot = arr[left];
  let swapIndex = left;

  for (let i = left + 1; i <= right; i++)
    if (pivot > arr[i])
      swap(arr, ++swapIndex, i);
  swap(arr, left, swapIndex);

  return swapIndex;
};
```

## `quickSort(arr)`

```js
const quickSort = (arr, left = 0, right = arr.length - 1) => {
  if (left < right) {
    let pivotIndex = pivot(arr, left, right);
    quickSort(arr, left, pivotIndex - 1);
    quickSort(arr, pivotIndex + 1, right);
  }

  return arr;
};
```
