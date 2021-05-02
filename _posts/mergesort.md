---
layout: post
title: Merge Sort Algorithim
---

When we look at the many sorting algorithims that are widely used to sort elements in a given array we use a comparison operator in order to rearrange the values until we have finished sorting an array. With all sorting algoritims we find that we compare some elements multiple times, but make little progress in re - arranging the elements in proper order. We find that in worst case scenarios, the amount of comparisons made can go up exponentially as the size increases, ruining efficency and increasing the runtime of these sorting algorithms.

In order to increase efficency and decrease the runtime in terms of bigO, we need to keep the comparisons of values to a minimum. In merge sort, we use a strategy of divide and conquer, where we divide the arrays into single length subarrays, and sort these subarrays and merging the parts together. By doing the comparisons in layers and merging in pairs, we are able to decrease the amount of total comparisons as arrays get larger and larger, whilist alternate algoritms such as quicksort may have fast average runtimes but suffer greaty in their worst case scenarios (O(n^2)) where merge sort has a runtime of O(nlogn) across all scenarios.


<pre>
              [38, 27, 43, 3, 9, 82, 10]   #recursive separation of array into halves until length of subarray is 1.
                      /          \        
                     /            \       
                    /              \
             [38, 27, 43, 3]     [9, 82, 10]
                 /     \            /   \   
                /       \          /     \   
            [38, 27]   [43, 3]  [9, 82]  [10]
            /     \     /   \    /    \     |
           [38]  [27] [43]  [3] [9]   [82] [10]  #the start of merging elements by comparing elements of subarray and 
             \     /    \    /    \    /    /     moving sorted elements into new subarray, recursively merging arrays
             [27, 38]   [3, 43]   [9, 82]  [10]   until merging is complete.
                \         /         \        /
              [3, 27, 38, 43]       [9, 10, 82]
                      \                  /
                   [3, 9, 10, 27, 38, 43, 82] #after 3 cycles of comparing elements and merging subarrays, we have sorted the                                                    array.
</pre>

The reason that merge sort has a runtime of O(nlogn) for arrays is because when we are starting the merging of the single elements, we compare in cycles, where we compare 2 elements in the whole array at most twice in a cycle. the number of cycles
that are used in merge sort is the log of the total number elements in the array, logn. Since we also take into consideration the number of elements in the array, the total runtime becomes logn * n, or O(nlogn). 


Here is some example code of merge sort:
```cpp
#include <iostream>
using namespace std;
 
void merge(int arr[], int l, int mid, int h)
{
    int n1 = mid - l + 1;
    int n2 = h - mid;
    //creating temporary arrays index [l - mid] and [mid - h]
    int L[n1], R[n2];
    
    for (int i = 0; i < n1; i++)
        L[i] = arr[l + i];
    for (int j = 0; j < n2; j++)
        R[j] = arr[m + 1 + j];
 
    //merging temp arrays back into one arr[l - h]
    int i = 0;
    int j = 0;
    int k = l;
    //merging loop
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) {
            arr[k] = L[i];
            i++;
        }
        else {
            arr[k] = R[j];
            j++;
        }
        k++;
    }
 
    while (i < n1) {
        arr[k] = L[i];
        i++;
        k++;
    }

    while (j < n2) {
        arr[k] = R[j];
        j++;
        k++;
    }
}

void mergeSort(int arr[],int l,int r){
    if(l >= r){
        return;
    }
    int m =l + (h - l)/2;
    mergeSort(arr,l , mid);
    mergeSort(arr ,mid + 1, h);
    merge(arr,l ,mid ,h);
}
 
void printArray(int A[], int size)
{
    for (int i = 0; i < size; i++)
        cout << A[i] << " ";
}
 

int main()
{
    int arr[] = {9, 3, 7, 5, 4, 8, 2};
    int len = sizeof(arr) / sizeof(arr[0]);
    printArray(arr, len);
    mergeSort(arr, 0, len - 1)
    printArray(arr, len);
    return 0;
}
```
