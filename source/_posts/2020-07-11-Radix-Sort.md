---
title: Radix Sort
date: 2020-07-11 17:31:12
tags: Algorithm
---

Radix Sort

```java
public static void radixSort(int[] arr) {
    int max = arr[0];
    for (int i = 1; i < arr.length; i++) {
        if(arr[i] > max) {
            max = arr[i];
        }
    }

    int maxLength = (max + "").length();

    //為防止放入數據的時候，數據溢出，每個桶的大小定為arr.length
    //基數排序是使用空間換時間的經典算法
    int[][] bucket = new int[10][arr.length];
    int[] bucketElementCount = new int[10]; //記錄各個桶每次放入數據的個數

    for (int i = 0, n = 1; i < maxLength; i++, n *= 10) {
        for (int j = 0; j < arr.length; j++) {
            int digitOfElement = arr[j] / n % 10;
            bucket[digitOfElement][bucketElementCount[digitOfElement]] = arr[j];
            bucketElementCount[digitOfElement]++;
        }

        int index = 0;
        for (int k = 0; k < bucket.length; k++) {
            if(bucketElementCount[k] != 0) {
                for (int l = 0; l < bucketElementCount[k]; l++) {
                    arr[index] = bucket[k][l];
                    index++;
                }
            }
            //把數據放回原數組後，重置每個bucketElementCount[k]
            bucketElementCount[k] = 0;
        }
    }
}
```

