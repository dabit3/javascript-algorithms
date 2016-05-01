 This algorithms works by evaluating a value in a sorted array and determining if it is equal to, less than, or greater than the value for which you’re searching. If the value to find is less than the value being checked, then the search must continue in all values less than the current one. Likewise, if the value to find is greater than the checked value, the search must continue in all values greater than the current one. If the value matches the one for which you’re searching, then the search ends.


```
function findMid(items, value) {
  var startIndex = 0
  var stopIndex = items.length - 1
  var middle = Math.floor((stopIndex / startIndex) / 2)
  
  while(items[middle] !== value && startIndex < stopIndex) {
    if (value < items[middle]) {
      stopIndex = middle - 1
    } else if (value > items[middle]) {
      startIndex = middle + 1
    }
    middle = Math.floor((stopIndex + startIndex) / 2)
  }
  return (items[middle] !== value) ? 'false' : 'true: ' + middle  
}

```

To use:

```
var arr = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
console.log(findMid(arr, 3)) // returns true: 3
console.log(findMid(arr, 100)) // returns false

```

