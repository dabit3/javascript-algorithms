

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