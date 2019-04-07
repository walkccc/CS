# Recursion Problem Set (hard)

## `reverse(str)`

> Write a recursive function called `reverse` which accepts a string and returns a new string in reverse.

```js
reverse('awesome'); // 'emosewa'
reverse('rithmschool'); // 'loohcsmhtir'
```

- Solution:

  ```js
  const reverse = str => {
    if (str.length <= 1) return str;
    return reverse(str.slice(1)) + str[0];
  };
  ```

## `isPalindrome(str)`

> Write a recursive function called `isPalindrome` which returns true if the string passed to it is a palindrome (reads the same forward and backward). Otherwise it returns false.

```js
isPalindrome('awesome'); // false
isPalindrome('foobar'); // false
isPalindrome('tacocat'); // true
isPalindrome('amanaplanacanalpanama'); // true
isPalindrome('amanaplanacanalpandemonium'); // false
```

- Solution:

  ```js
  const isPalindrome = str => {
    if (str.length == 1) return true;
    if (str.length == 2) return str[0] == str[1];
    if (str[0] === str.slice(-1)) return isPalindrome(str.slice(1, -1));
    return false;
  };
  ```

## `someRecursive(arr, callback)`

> Write a recursive function called `someRecursive` which accepts an array and a callback. The function returns true if a single value in the array returns true when passed to the callback. Otherwise it returns false.

```js
const isOdd = val => val % 2 !== 0;
someRecursive([1, 2, 3, 4], isOdd); // true
someRecursive([4, 6, 8, 9], isOdd); // true
someRecursive([4, 6, 8], isOdd); // false
someRecursive([4, 6, 8], val => val > 10); // false
```

- Solution:

  ```js
  const someRecursive = (arr, callback) => {
    if (callback(arr[0])) return true;
    if (arr.length == 1) return callback(arr[0]);
    return someRecursive(arr.slice(1), callback);
  };
  ```

## `flatten`

> Write a recursive function called `flatten` which accepts an array of arrays and returns a new array with all values flattened.

```js
flatten([1, 2, 3, [4, 5]]); // [1, 2, 3, 4, 5]
flatten([1, [2, [3, 4], [[5]]]]); // [1, 2, 3, 4, 5]
flatten([[1], [2], [3]]); // [1, 2, 3]
flatten([[[[1], [[[2]]], [[[[[[[3]]]]]]]]]]); // [1, 2, 3]
```

- Solution:

  ```js
  const flatten = oldArr => {
    let newArr = [];
    for (let i = 0; i < oldArr.length; i++) {
      if (Array.isArray(oldArr[i])) {
        newArr = newArr.concat(flatten(oldArr[i]));
      } else {
        newArr = [...newArr, oldArr[i]];
      }
    }
    return newArr;
  };
  ```

## `capitalizeFirst`

> Write a recursive function called `capitalizeFirst`. Given an array of strings, capitalize the first letter of each string in the array.

```js
capitalizeFirst(['car', 'taco', 'banana']); // ['Car', 'Taco', 'Banana']
```

- Solution:

```

```
