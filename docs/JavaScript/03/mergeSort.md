# Merge Sort

## `merge(arr1, arr2)`

```js
const merge = (arr1, arr2) => {
  let ret = [];
  let i = 0;
  let j = 0;

  while (i < arr1.length && j < arr2.length) {
    if (arr1[i] < arr2[j]) ret.push(arr1[i++]);
    else ret.push(arr2[j++]);
  }

  while (i < arr1.length) ret.push(arr1[i++]);
  while (j < arr2.length) ret.push(arr2[j++]);

  return ret;
};
```

## `mergeSort(arr)`

```js
const mergeSort = arr => {
  if (arr.length <= 1) return arr;

  let mid = Math.floor(arr.length / 2);
  let left = mergeSort(arr.slice(0, mid));
  let right = mergeSort(arr.slice(mid));

  return merge(left, right);
};
```
