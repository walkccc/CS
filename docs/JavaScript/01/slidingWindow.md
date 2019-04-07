# Sliding Window Pattern

This pattern involves creating a **window** which can either be an array or number from one position to another.

Depending on a certain condition, the window either increases or closes (and a new window is created).

Very useful for keeping track of a subset of data in an array/string etc.

---

## `maxSubarraySum(arr, n)`

> Write a function called `maxSubarraySum` which accepts an array of integers and a number called **n**. The function should calculate the maximum sum of **n** consecutive elements in the array.

```js
maxSubarraySum([1, 2, 5, 2, 8, 1, 5], 2); // 10
maxSubarraySum([1, 2, 5, 2, 8, 1, 5], 4); // 17
maxSubarraySum([4, 2, 1, 6], 1); // 6
maxSubarraySum([], 4); // null
```

- Solution 1 (naive):

    - Time: $O(n^2)$

    ```js
    const maxSubarraySum = (arr, n) => {
      if (n > arr.length) return null;

      let ret = -Infinity;

      for (let i = 0; i < arr.length - n + 1; i++) {
        let temp = 0;
        for (let j = 0; j < n; j++)
          temp += arr[i + j];

        ret = Math.max(ret, temp);
      }

      return ret;
    };
    ```

- Solution 2 (refactor):

    - Time: $O(n)$
    - Space: $O(1)$

    ```js
    const maxSubarraySum = (arr, n) => {
      if (arr.length < n) return null;

      let ret = 0;
      let temp = 0;

      for (let i = 0; i < n; i++) ret += arr[i];
      
      temp = ret;
      for (let i = n; i < arr.length; i++) {
        temp = temp - arr[i - n] + arr[i];
        ret = Math.max(ret, temp);
      }

      return ret;
    };
    ```

## `minSubArrayLen(arr, num)`

> Write a function called `minSubArrayLen` which accepts two parameters - an array of positive integers and a positive integer.
>
> This function should return the minimal length of a contiguous subarray of which the sum is greater than or equal to the integer passed to the function. If there isn’t one, return 0 instead.

```js
minSubArrayLen([2, 3, 1, 2, 4, 3], 7); // 2 -> because [4, 3] is the smallest subarray
minSubArrayLen([2, 1, 6, 5, 4], 9); // 2 -> because [5, 4] is the smallest subarray
minSubArrayLen([3, 1, 62, 19], 52); // 1 -> because [62] is greater than 52
```

- Solution

    - Time: $O(n)$
    - Space: $O(1)$

    ```js
    const minSubArrayLen = (arr, num) => {
      let i = 0; // start
      let j = 0; // end
      let sum = 0;
      let ret = Infinity;

      while (i < arr.length) {
        if (sum < num && j < arr.length) {
          sum += arr[j];
          j++;
        } else if (sum >= num) {
          ret = Math.min(ret, j - i);
          sum -= arr[i];
          i++;
        } else {
          break;
        }
      }

      return ret === Infinity ? 0 : ret;
    };
    ```

## `findLongestSubstring(str)`

> Write a function called `findLongestSubstring`, which accepts a string and returns the length of the longest substring with all distinct characters.

```js
findLongestSubstring(''); // 0
findLongestSubstring('rithmschool'); // 7
findLongestSubstring('thecatinthehat'); // 7
findLongestSubstring('bbbbbb'); // 1
```

- Solution:

    - Time: $O(n)$

    ```js
    const findLongestSubstring = str => {
      let ret = 0;
      let seen = {};
      let i = 0;

      for (let j = 0; j < str.length; j++) {
        let char = str[j];
        if (seen[char]) i = Math.max(i, seen[char]);
        ret = Math.max(ret, j - i + 1);
        seen[char] = j + 1;
      }

      return ret;
    };
    ```
