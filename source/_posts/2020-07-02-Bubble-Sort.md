---
title: Bubble Sort
date: 2020-07-02 19:51:21
tags: Algorithm
---

Bubble Sort

```java
public static void bubbleSort(int[] arr) {
    int temp = 0;
    boolean flag = false;
    for (int i = 0; i < arr.length - 1; i++) {
        for (int j = 0; j < arr.length - 1 - i; j++) {
            if(arr[j] > arr[j + 1]) {
                flag = true;
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
        //            System.out.printf("第%d趟排序後的結果",i+1);
        //            System.out.println(Arrays.toString(arr));
        if(!flag) {
            break;
        } else {
            flag = false;
        }
    }
}
```

