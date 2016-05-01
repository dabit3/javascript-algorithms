From [Wikipedia](https://en.wikipedia.org/wiki/Binary_heap):

A binary heap is a heap data structure created using a binary tree. It can be seen as a binary tree with two additional constraints:

#### Shape property
A binary heap is a complete binary tree; that is, all levels of the tree, except possibly the last one (deepest) are fully filled, and, if the last level of the tree is not complete, the nodes of that level are filled from left to right.

#### Heap property
All nodes are either greater than or equal to or less than or equal to each of its children, according to a comparison predicate defined for the heap.

```
var binaryHeap = function(comp) {

  comp = comp || function(a, b) {
    return a > b
  }

  var arr = []

  var swap = function(a, b) {
    var temp = arr[a]
    arr[a] = arr[b]
    arr[b] = temp
  }

  var bubbleDown = function(pos) {
    var left = 2 * pos + 1
    var right = left + 1
    var largest = pos
    if (left < arr.length && comp(arr[left], arr[largest])) {
      largest = left
    }
    if (right < arr.length && comp(arr[right], arr[largest])) {
      largest = right
    }
    if (largest != pos) {
      swap(largest, pos)
      bubbleDown(largest)
    }
  }

  var bubbleUp = function(pos) {
    if (pos <= 0) {
      return
    }
    var parent = Math.floor((pos - 1) / 2)
    if (comp(arr[pos], arr[parent])) {
      swap(pos, parent)
      bubbleUp(parent)
    }
  }

  var heap = {}

  heap.pop = function() {
    if (arr.length === 0) {
      throw new Error("pop() called on emtpy binary heap")
    }
    var value = arr[0]
    var last = arr.length - 1
    arr[0] = arr[last]
    arr.length = last
    if (last > 0) {
      bubbleDown(0)
    }
    return value
  }

  heap.push = function(value) {
    arr.push(value)
    bubbleUp(arr.length - 1)
  }

  heap.size = function() {
    return arr.length
  }
  
  heap.get = function() {
    return arr
  }
  
  return heap
}

```
Implementation: Default comparison operator (largest to smallest)

```
var bh = binaryHeap()
bh.push(5)
bh.push(34)
bh.push(16)
bh.pop()
console.log("number in heap: " + bh.size())
console.log('bh', bh.get())
console.log("number in heap: " + bh.size())
```

Implementation: Custom comparison operator (smallest to largest)

```
var bh2 = binaryHeap(function(a, b) {
  return a < b
})

bh2.push(99)
bh2.push(9)
bh2.push(990)
bh2.push(100)

console.log("number in heap2: " + bh2.size())
console.log('bh2', bh2.get())

```