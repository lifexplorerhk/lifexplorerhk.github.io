---
title: Merge Sort
date: 2020-07-06 21:43:16
tags: Algorithm
---

Merge Sort

```java
public static void mergeSort(int[] arr, int left, int right, int[] temp) {
    if(left < right) {
        int mid = (left + right) / 2;
        mergeSort(arr, left, mid, temp);
        mergeSort(arr, mid + 1, right, temp);
        merge(arr,left,mid,right,temp);
    }
}

public static void merge(int[] arr, int left, int mid, int right, int[] temp) {
    int i = left;
    int j = mid + 1;
    int t = 0;

    while(i <= mid && j <= right) {
        if(arr[i] <= arr[j]) {
            temp[t] = arr[i];
            t++;
            i++;
        } else {
            temp[t] = arr[j];
            t++;
            j++;
        }
    }

    while(i <= mid) {
        temp[t] = arr[i];
        t++;
        i++;
    }

    while(j <= right) {
        temp[t] = arr[j];
        t++;
        j++;
    }

    t = 0;
    int tempLeft = left;
    while(tempLeft <= right) {
        arr[tempLeft] = temp[t];
        t++;
        tempLeft++;
    }
}
```

