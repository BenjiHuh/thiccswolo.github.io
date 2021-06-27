---
layout: post
title: Heapsort and Priority Queues
---

Heap sort is a sorting method that is mainly used from binary heap data structures. In order to get a better understanding of Heap Sort and Priority Queue, it will help 
to know the following concepts; a complete binary tree, how heaps are represented in an array, and max and min heap. All these concepts can be thoroughly in Abdul Bari's lecture on Heap:
https://www.youtube.com/watch?v=HqPJF2L5h9U

How to use heap sort algorithim (steps): 
1. Build a max heap from the input given.
2. At this point, the largest item is stored at the root of the heap. Replace it with the last item of the heap followed by reducing the size of heap by 1. 
Finally, heapify the root of the tree. 
3. Repeat step 2 while the size of the heap is greater than 1.

Why use heap sort?
While sorting algorithims such as quicksort are widely used, for those that aren't in need of the fastest possible sorting algorithim and need reliable results, heap sort not only uses far less memory by not utilizing more than 1 extra array, but heap sort's runtime is always O(nlogn), unlike quicksort's worst case of O(n^2). This gives heap sort an edge when comparing worse-case scenarios for extra large data sets.

What is priority queue?

priority queue is similar to a regular queue or a stack in which there is some form of data type that can stack or enqueue an element and pop or dequeue an element at the end of the aforementioned queue or stack. In priotiry queue, there is an additional element considered, the priority value of an element that affects which element would be dequeued next.

The reason priority queue and heapsort are often associated with is because they both utilize the heap data structure, which is especially useful in priority queue, where there is a priority element in which element is deqeued next. In priority queue specifically, the need to have fast runtimes for inserting elements, setting the highest priority element to be selected, and finding the value of the highest priority element. The binary heap is extremely useful for priority queues, where the insertion and max-heaping of a heap will only take O(logn) time, and finding the value of the next dequeued element will be O(1), as the max - heap or min - heap will always put the next value on top of the heap.

This is some example code in Java for Heap Sort from the Geeksforgeeks Website;

```java
// Java program for implementation of Heap Sort
public class HeapSort
{
    public void sort(int arr[])
    {
        int n = arr.length;
  
        // Build heap (rearrange array)
        for (int i = n / 2 - 1; i >= 0; i--)
            heapify(arr, n, i);
  
        // One by one extract an element from heap
        for (int i=n-1; i>=0; i--)
        {
            // Move current root to end
            int temp = arr[0];
            arr[0] = arr[i];
            arr[i] = temp;
  
            // call max heapify on the reduced heap
            heapify(arr, i, 0);
        }
    }
  
    // To heapify a subtree rooted with node i which is
    // an index in arr[]. n is size of heap
    void heapify(int arr[], int n, int i)
    {
        int largest = i;  // Initialize largest as root
        int l = 2*i + 1;  // left = 2*i + 1
        int r = 2*i + 2;  // right = 2*i + 2
  
        // If left child is larger than root
        if (l < n && arr[l] > arr[largest])
            largest = l;
  
        // If right child is larger than largest so far
        if (r < n && arr[r] > arr[largest])
            largest = r;
  
        // If largest is not root
        if (largest != i)
        {
            int swap = arr[i];
            arr[i] = arr[largest];
            arr[largest] = swap;
  
            // Recursively heapify the affected sub-tree
            heapify(arr, n, largest);
        }
    }
  
    /* A utility function to print array of size n */
    static void printArray(int arr[])
    {
        int n = arr.length;
        for (int i=0; i<n; ++i)
            System.out.print(arr[i]+" ");
        System.out.println();
    }
  
    // Driver program
    public static void main(String args[])
    {
        int arr[] = {12, 11, 13, 5, 6, 7};
        int n = arr.length;
  
        HeapSort ob = new HeapSort();
        ob.sort(arr);
  
        System.out.println("Sorted array is");
        printArray(arr);
    }
}
```
