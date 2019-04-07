# Divide and Conquer Pattern

This pattern involves dividing a data set into smaller chunks and then repeating a process with a subset of data.

This pattern can tremendously **decrease time complexity**.

---

## `search(arr, val)`

> Given a **sorted** array of integers, write a function called `search`, that accepts a value and returns the index where the value passed to the function is located. If the value is not found, return -1.

```js
search([1, 2, 3, 4, 5, 6], 4); // 3
search([1, 2, 3, 4, 5, 6], 6); // 5
search([1, 2, 3, 4, 5, 6], 11); // -1
```

- Solution 1 (naive)

  - Time: $O(n)$

  ```js
  const search = (arr, val) => {
    for (let i = 0; i < arr.length; i++)
      if (arr[i] === val)
        return i;
    return -1;
  };
  ```

- Solution 2 (binary search)

  - Time: $O(\log n)$

  ```js
  const search = (arr, val) => {
    let left = 0;
    let right = arr.length - 1;

    while (left <= right) {
      let mid = Math.floor((left + right) / 2);
      let curr = arr[mid];

      if (arr[mid] < val) {
        left = mid + 1;
      } else if (arr[mid] > val) {
        right = mid - 1;
      } else {
        return mid;
      }
    }

    return -1;
  };
  ```
