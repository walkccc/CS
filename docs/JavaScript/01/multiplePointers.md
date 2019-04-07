# Multiple Pointers Pattern

Creating **pointers** or values that correspond to an index or position and move towards the beginning, end or middle based on a certain condition.

**Very** efficient for solving problems with minimal Space as well.

---

## `sumZero(arr)`

> Write a function called `sumZero` which accepts a **sorted** array of integers. The function should find the **first** pair where the sum is 0. Return an array that includes both values that sum to zero or undefined if a pair does not exist.

```js
sumZero([-3, -2, -1, 0, 1, 2, 3]); // [-3, 3]
sumZero([-2, 0, 1, 3]); // undefined
sumZero([1, 2, 3]); // undefined
```

- Solution 1 (naive)

    - Time: $O(n^2)$
    - Space: $O(1)$

    ```js
    const sumZero = arr => {
      for (let i = 0; i < arr.length; i++)
        for (let j = i + 1; j < arr.length; j++)
          if (arr[i] + arr[j] === 0)
            return [arr[i], arr[j]];
    };
    ```

- Solution 2 (refactor):

    - Time: $O(n)$
    - Space: $O(1)$

    ```js
    const sumZero = arr => {
      let left = 0;
      let right = arr.length - 1;

      while (left < right) {
        let sum = arr[left] + arr[right];

        if (sum === 0) return [arr[left], arr[right]];
        else if (sum < 0) left++;
        else right--;
      }
    };
    ```

## `countUniqueValues(arr)`

> Implement a function called `countUniqueValues`, which accepts a sorted array, and counts the unique values in the array. There can be negative numbers in the array, but it will always be sorted.

```js
countUniqueValues([1, 1, 1, 1, 1, 2]); // 2
countUniqueValues([-2, -1, -1, 0, 1]); // 4
countUniqueValues([]); // 0
```

- Solution:

    - Time: $O(n)$
    - Space: $O(1)$

    ```js
    const countUniqueValues = arr => {
      if (arr.length === 0) return 0;

      let i = 0;
      for (let j = 1; j < arr.length; j++)
        if (arr[i] !== arr[j])
          arr[++i] = arr[j];

      return i + 1;
    };
    ```

## `averagePair(arr, val)`

> Write a function called `averagePair`. Given a sorted array of integers and a target average, determine if there is a pair of values in the array where the average of the pair equals the target average. There may be more than one pair that matches the average target.

```js
averagePair([1, 2, 3], 2.5); // true
averagePair([1, 3, 3, 5, 6, 7, 10, 12, 19], 8); // true
averagePair([-1, 0, 3, 4, 5, 6], 4.1); // false
averagePair([], 4); // false
```

- Solution:

    - Time: $O(n)$
    - Space: $O(1)$

    ```js
    const averagePair = (arr, num) => {
      let left = 0;
      let right = arr.length - 1;

      while (left < right) {
        let average = (arr[left] + arr[right]) / 2;

        if (average === num) return true;
        else if (average < num) left++;
        else right--;
      }

      return false;
    };
    ```

## `isSubsequence(str1, str2)`

> Write a function called `isSubsequence` which takes in two strings and checks whether the characters in the first string form a subsequence of the characters in the second string. In other words, the function should check whether the characters in the first string appear somewhere in the second string, **without their order changing**.

```js
isSubsequence('hello', 'hello world'); // true
isSubsequence('sing', 'sting'); // true
isSubsequence('abc', 'acb'); // false (order matters)
```

- Solution 1 (iterative):

    - Time: $O(n + m)$
    - Space: $O(1)$

    ```js
    const isSubsequence = (str1, str2) => {
      if (!str1) return true;
  
      let i = 0;
      for (let j = 0; j < str2.length; j++) {
        if (i == str1.length - 1) return true;
        if (str1[i] === str2[j]) i++;
      }
  
      return false;
    };
    ```

- Solution 2 (recursive but not $O(1)$ space):

    ```js
    const isSubsequence = (str1, str2) => {
      if (str1.length === 0) return true;
      if (str2.length === 0) return false;
      if (str2[0] === str1[0]) return isSubsequence(str1.slice(1), str2.slice(1));
      return isSubsequence(str1, str2.slice(1));
    };
    ```
