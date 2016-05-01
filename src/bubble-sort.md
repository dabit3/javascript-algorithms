From [Wikipedia](https://en.wikipedia.org/wiki/Bubble_sort):

Bubble sort, sometimes referred to as sinking sort, is a simple sorting algorithm that repeatedly steps through the list to be sorted, compares each pair of adjacent items and swaps them if they are in the wrong order. The pass through the list is repeated until no swaps are needed, which indicates that the list is sorted. The algorithm, which is a comparison sort, is named for the way smaller elements "bubble" to the top of the list. Although the algorithm is simple, it is too slow and impractical for most problems even when compared to insertion sort. It can be practical if the input is usually in sorted order but may occasionally have some out-of-order elements nearly in position.


**Our implementation takes one function, swap:**

```
function swap(items, firstIndex, secondIndex){
    var temp = items[firstIndex]
    items[firstIndex] = items[secondIndex]
    items[secondIndex] = temp
}
```
#### Implementation #1

```
function bubbleSort(items) {
    var len = items.length,
        i, j, stop
    for (i=0; i < len; i++){
        for (j=0, stop=len-i; j < stop; j++){
            if (items[j] > items[j+1]){
                swap(items, j, j+1)
            }
        }
    }
    return items;
}
```

#### Implementation #2

```
function bubbleSort(items) {
    var len = items.length,
        i, j

    for (i=len-1; i >= 0; i--){
        for (j=len-i; j >= 0; j--){
            if (items[j] < items[j-1]){
                swap(items, j, j-1)
            }
        }
    }

    return items
}
```
To use:

```
var arr= [10, 100, 1, 1000, 5, 50, 500, 5000]
console.log(bubbleSort(arr))

```