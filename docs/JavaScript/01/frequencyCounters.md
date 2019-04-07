# Frequency Counters Pattern

This pattern uses objects or sets to collect values/frequencies of values.

This can often avoid the need for nested loops or $O(n^2)$ operations with arrays/strings.

---

## `same(arr1, arr2)`

> Write a function called `same`, which accepts two arrays. The function should return true if every value in the array has it's corresponding value squared in the second array. The frequency of values must be the same.

```js
same([1, 2, 3], [4, 1, 9]); // true
same([1, 2, 3], [1, 9]); // false
same([1, 2, 1], [4, 4, 1]); // false (must be same frequency)
```

- Solution 1 (naive)

    - Time: $O(n^2)$
    - Space: $O(1)$

    ```js
    const same = (arr1, arr2) => {
      if (arr1.length !== arr2.length) return false;

      for (let i = 0; i < arr1.length; i++) {
        let correctIndex = arr2.indexOf(arr1[i] ** 2);
        if (correctIndex === -1) return false;
        arr2.splice(correctIndex, 1);
      }

      return true;
    };
    ```

- Solution 2 (refactor)

    - Time: $O(n)$
    - Space: $O(n)$

    ```js
    const same = (arr1, arr2) => {
      if (arr1.length !== arr2.length) return false;

      const freqCount1 = {};
      const freqCount2 = {};
      
      for (let val of arr1) freqCount1[val] = (freqCount1[val] || 0) + 1;
      for (let val of arr2) freqCount2[val] = (freqCount2[val] || 0) + 1;
      for (let key in freqCount1) {
        if (!(key ** 2 in freqCount2)) return false;
        if (freqCount1[key] !== freqCount2[key ** 2]) return false;
      }

      return true;
    };
    ```

## `validAnagram(arr1, arr2)`

> Given two strings, write a function called `validAnagram` to determine if the second string is an anagram of the first. An anagram is a word, phrase, or name formed by rearranging the letters of another, such as _cinema_, formed from _iceman_.

```js
validAnagram('', ''); // true
validAnagram('aaz', 'zza'); // false
validAnagram('anagram', 'nagaram'); // true
```

- Solution

    - Time: $O(n)$
    - Space: $O(n)$

    ```js
    const validAnagram = (arr1, arr2) => {
      if (arr1.length !== arr2.length) return false;

      const freqCount1 = {};

      for (let val of arr1) freqCount1[val] = (freqCount1[val] || 0) + 1;
      for (let val of arr2) {
        if (!freqCount1[val]) return false;
        freqCount1[val]--;
      }

      return true;
    };
    ```

## `sameFrequency(num1, num2)`

> Write a function called `sameFrequency`. Given two positive integers, find out if the two numbers have the same frequency of digits.

```js
sameFrequency(182, 281); // true
sameFrequency(3589578, 5879385); // true
sameFrequency(34, 14); // false
sameFrequency(22, 222); // false
```

- Solution

    - Time: $O(n)$

    ```js
    const sameFrequency = (num1, num2) => {
      strNum1 = num1.toString();
      strNum2 = num2.toString();

      if (strNum1.length !== strNum2.length) return false;

      const freqCount1 = {};

      for (let val of strNum1) freqCount1[val] = (freqCount1[val] || 0) + 1;
      for (let val of strNum2) {
        if (!freqCount1[val]) return false;
        freqCount1[val]--;
      }

      return true;
    };
    ```

## `areThereDuplicates(...args)`

> Implement a function called, `areThereDuplicates` which accepts a variable number of arguments, and checks whether there are any duplicates among the arguments passed in. You can solve this using the frequency counter pattern OR the multiple pointers pattern.

```js
areThereDuplicates(1, 2, 3); // false
areThereDuplicates(1, 2, 2); // true
areThereDuplicates('a', 'b', 'c', 'a'); // true
```

- Solution 1 (frequency counter)

    - Time: $O(n)$
    - Space: $O(n)$

    ```js
    const areThereDuplicates = (...args) => {
      let lookup = {};

      for (let val of args) {
        if (lookup[val]) return true;
        lookup[val] = (lookup[val] || 0) + 1;
      }

      return false;
    };
    ```

- Solution 2 (multiple pointers)

    - Time: $O(n\log n)$
    - Space: $O(1)$

    ```js
    const areThereDuplicates = (...args) => {
      args.sort();

      let i = 0;

      for (let j = 1; j < args.length; i++, j++)
        if (args[i] === args[j])
          return true;

      return false;
    };
    ```

- Solution 3

    ```js
    const areThereDuplicates = () => {
      return new Set(arguments).size !== arguments.length;
    };
    ```
