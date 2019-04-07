# Recursion Problem Set (easy)

## `power(n, x)`

> Write a function called `power` which accepts a base and an exponent. The function should return the power of the base to the exponent.
> This function should mimic the functionality of `Math.pow()` - do not worry about negative bases and exponents.

```js
const power = (n, x) => {
  if (x == 0) return 1;
  if (x == 1) return n;
  let t = power(n, Math.floor(x / 2));
  return t * t * power(n, x % 2);
};
```

## `factorial(n)`

> Write a function `factorial` which accepts a number and returns the factorial of that number. A factorial is the product of an integer and all the integers below it; e.g., factorial four (4!) is equal to 24, because 4 \* 3 \* 2 \* 1 equals 24. **factorial zero (0!) is always 1.**

```js
const factorial = n => {
  if (n == 0) return 1;
  return n * factorial(n - 1);
};
```

## `productOfArray(arr)`

> Write a function called `productOfArray` which takes in an array of numbers and returns the product of them all.

```js
const productOfArray = arr => {
  if (arr.length == 0) return 1;
  return arr[0] * productOfArray(arr.splice(1));
};
```

## `recursiveRange(num)`

> Write a function called `recursiveRange` which accepts a number and adds up all the numbers from 0 to the number passed to the function.

```js
const recursiveRange = num => {
  if (num == 0) return 0;
  return num + recursiveRange(num - 1);
};
```

## `fib(num)`

> Write a recursive function called `fib` which accepts a number and returns the nth number in the Fibonacci sequence. Recall that the Fibonacci sequence is the sequence of whole numbers 1, 1, 2, 3, 5, 8, which starts with 1 and 1, and where every number thereafter is equal to the sum of the previous two numbers.

```js
const fib = num => {
  if (num == 1 || num == 2) return 1;
  return fib(num - 1) + fib(num - 2);
};
```
