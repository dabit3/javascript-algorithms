From [Wikipedia](https://en.wikipedia.org/wiki/Selection_sort):

In computer science, selection sort is a sorting algorithm, specifically an in-place comparison sort. It has O(n2) time complexity, making it inefficient on large lists, and generally performs worse than the similar insertion sort. Selection sort is noted for its simplicity, and it has performance advantages over more complicated algorithms in certain situations, particularly where auxiliary memory is limited.:

```
function findSmallest (arr) {
  smallest = arr[0]
  smallest_index = 0
  for (var i = 0; i < arr.length; i++) {
    if (arr[i] < smallest) {
      smallest = arr[i]
      smallest_index = i
    }
  }
  return arr[smallest_index]
}

function selectionSort (arr) {
  var newArr = []
  var i = 0
  while (i < arr.length) {
    var smallest = findSmallest(arr)
    var a = arr.splice(arr.indexOf(smallest), 1)
    console.log('newArr:', newArr)
    console.log('arr::::', arr)
    newArr.push(a[0])
  }
  return newArr
}

```
To use:

```
var tempArr = []

for (var i = 90; i < 100; i++) {
  tempArr.push(i)
}

tempArr.push(9999)
tempArr.push(47)
tempArr.push(1012)
tempArr.push(89)
tempArr.push(19)

console.log(selectionSort(tempArr))

```