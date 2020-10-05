---
title: Shell Sort
date: 2020-07-05 10:49:58
tags: Algorithm
---

Shell Sort

```java
//交換式的希爾排序法
public static void shellSort(int[] arr) {
    int temp = 0;

    for (int gap = arr.length / 2; gap > 0; gap /= 2) {
        for (int i = gap; i < arr.length; i++) {
            for (int j = i - gap; j >= 0 ; j -= gap) {
                if(arr[j] > arr[j + gap]) { //如果當前元素大於加上步長後的元素，進行交換
                    temp = arr[j];
                    arr[j] = arr[j + gap];
                    arr[j + gap] = temp;
                }
            }
        }
    }
}

//移位式的希爾排序法
public static void improvedShellSort(int[] arr) {
    for (int gap = arr.length / 2; gap > 0; gap /= 2) {
        //從第gap個元素開始，逐個對其所在的組進行插入排序
        for (int i = gap; i < arr.length; i++) {
            int j = i;
            int temp = arr[j];
            if(arr[j] < arr[j - gap]) {
                while(j - gap >= 0 && temp < arr[j - gap]) {
                    arr[j] = arr[j - gap];
                    j -= gap;
                }
                arr[j] = temp;
            }
        }
    }
}
```

