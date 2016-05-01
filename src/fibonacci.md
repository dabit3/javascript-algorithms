From [Wikipedia](https://en.wikipedia.org/wiki/Fibonacci_number):<br />
In mathematics, the Fibonacci numbers or Fibonacci sequence are the numbers in the following integer sequence:

1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...
or (often, in modern usage):

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...

The Fibonacci spiral: an approximation of the golden spiral created by drawing circular arcs connecting the opposite corners of squares in the Fibonacci tiling; this one uses squares of sizes 1, 1, 2, 3, 5, 8, 13, 21, and 34.
By definition, the first two numbers in the Fibonacci sequence are either 1 and 1, or 0 and 1, depending on the chosen starting point of the sequence, and each subsequent number is the sum of the previous two.

```
function fibonacci (n) {
    if (n > 97) {
      throw 'Input too large...'
    }
    var n1 = 0
    var n2 = 1
    var aux

    while (n > 0) {
      aux = n1
      n1 = n2
      n2 += aux
      n = n - 1
    }

    return n1
  }

```
To use:

```
var num = fibonacci(18)

console.log('num: ', num)

```