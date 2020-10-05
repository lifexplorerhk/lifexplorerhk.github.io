---
title: Insertion Sort
date: 2020-07-02 21:09:27
tags: Algorithm
---

Insertion Sort

```java
public static void insertionSort(int[] arr) {
    for (int i = 1; i < arr.length; i++) {
        int insertVal = arr[i]; //先保存待插入的數值
        int insertIndex = i - 1; //準備與前一個數進行比較

        while(insertIndex >= 0 && insertVal < arr[insertIndex]) {
            arr[insertIndex + 1] = arr[insertIndex];
            insertIndex--;
        }

        if(insertIndex + 1 != i) {
            arr[insertIndex + 1] = insertVal;
        }
    }
}
```

