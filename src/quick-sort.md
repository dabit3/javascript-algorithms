From [Wikipedia](https://en.wikipedia.org/wiki/Quicksort):<br />
Quicksort is a comparison sort, meaning that it can sort items of any type for which a "less-than" relation (formally, a total order) is defined. In efficient implementations it is not a stable sort, meaning that the relative order of equal sort items is not preserved. Quicksort can operate in-place on an array, requiring small additional amounts of memory to perform the sorting.

Mathematical analysis of quicksort shows that, on average, the algorithm takes O(n log n) comparisons to sort n items. In the worst case, it makes O(n2) comparisons, though this behavior is rare.

**Our quicksort algorithm takes two functions, swap and partition:**

```
function swap(items, firstIndex, secondIndex){
    let temp = items[firstIndex]
    items[firstIndex] = items[secondIndex]
    items[secondIndex] = temp
}

function partition(items, left, right) {
    let pivot   = items[Math.floor((right + left) / 2)],
        i       = left,
        j       = right
    while (i <= j) {
        while (items[i] < pivot) {
            i++
        }
        while (items[j] > pivot) {
            j--
        }
        if (i <= j) {
            swap(items, i, j)
            i++
            j--
        }
    }
    return i
}

function quickSort(items, left, right) {
    let index
    if (items.length > 1) {
        index = partition(items, left, right);
        if (left < index - 1) {
            quickSort(items, left, index - 1);
        }
        if (index < right) {
            quickSort(items, index, right);
        }
    }
    return items
}
```

To use:

```
let arr= [10, 100, 1, 1000, 5, 50, 500, 5000]
console.log(quickSort(arr, 0, arr.length - 1))

```
