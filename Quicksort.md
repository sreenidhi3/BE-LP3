# Randomized and Deterministic Quicksort
#### Time Complexity -> 
 - O(nlogn) - Randomized Quicksort (assumption - all elements are not same)
 - O(n^2) - Deterministic Quicksort

#### Space Complexity -> 
 - O(nlogn) - Randomized Quicksort 
 - O(nlogn) - Deterministic Quicksort

O(log n) is used for storing call stack formed due to recursion
```
import random

def quicksort(arr, start , stop):
    if(start < stop):
        pivotindex = partitionrand(arr, start, stop)
        quicksort(arr , start , pivotindex-1)
        quicksort(arr, pivotindex + 1, stop)
        
def partitionrand(arr , start, stop):
# generates random pivot swaps the first element with the pivot
    randpivot = random.randrange(start, stop)
    arr[start], arr[randpivot] = arr[randpivot], arr[start]
    return partition(arr, start, stop)
    
'''
take the first element as pivot, and all the elements are re-arranged
such that the elements smaller than the pivot appear on the left 
and the elements greater than the pivot are to the right of pivot.
'''
def partition(arr,start,stop):
    pivot = start 
    i = start + 1
    for j in range(start + 1, stop + 1):
        if arr[j] <= arr[pivot]:
            arr[i] , arr[j] = arr[j] , arr[i]
            i = i + 1
            arr[pivot] , arr[i - 1] = arr[i - 1] , arr[pivot]
            pivot = i - 1
    return (pivot)

array = [10, 7, 8, 9, 1, 5]
quicksort(array, 0, len(array) - 1)
print(array)

```
