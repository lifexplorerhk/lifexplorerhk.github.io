---
title: Selection Sort
date: 2020-07-02 20:21:38
tags: Algorithm
---

Selection Sort

```java
public static void selectionSort(int[] arr) {
    for (int i = 0; i < arr.length - 1; i++) {
        int minIndex = i;
        int min = arr[minIndex];
        for (int j = i + 1; j < arr.length; j++) {
            if(min > arr[j]) {
                min = arr[j];
                minIndex = j;
            }
        }
        if(minIndex != i) {
            arr[minIndex] = arr[i];
            arr[i] = min;
        }
    }
}
```

