---
title: Quick Sort
date: 2020-07-05 17:09:03
tags: Algorithm
---

Quick Sort

```java
public static void quickSort(int[] arr, int left, int right) {
    int l = left;
    int r = right;
    int pivot = arr[(left + right) / 2];
    int temp = 0;

    while(l < r) {
        //在pivot左邊一直找，直到找到大於或等於pivot值，才退出
        while(arr[l] < pivot) {
            l++;
        }
        //在pivot右邊一直找，直到找到小於或等於pivot值，才退出
        while(arr[r] > pivot) {
            r--;
        }

        if(l >= r) {
            break;
        }

        temp = arr[l];
        arr[l] = arr[r];
        arr[r] = temp;

        if(arr[l] == pivot) {
            r--;
        }

        if(arr[r] == pivot) {
            l++;
        }
    }

    //如果l == r，必須l++，r--，否則會棧溢出
    if(l == r) {
        l++;
        r--;
    }

    if(left < r) {
        quickSort(arr, left, r);
    }

    if(right > l) {
        quickSort(arr, l, right);
    }
}
```

