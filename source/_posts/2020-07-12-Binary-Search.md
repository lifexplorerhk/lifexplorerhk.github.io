---
title: Binary Search
date: 2020-07-12 10:45:35
tags: Algorithm
---

Binary Search

```java
public static int binarySearch(int[] arr, int left, int right, int findVal) {
    if(left > right) {
        return -1;
    }

    int mid = (left + right) / 2;
    int midVal = arr[mid];

    if(findVal > midVal) {
        return binarySearch(arr, mid + 1, right, findVal);
    } else if(findVal < midVal) {
        return binarySearch(arr, left, mid - 1, findVal);
    } else {
        return mid;
    }
}

public static List<Integer> binarySearch2(int[] arr, int left, int right, int findVal) {
    if(left > right) {
        return new ArrayList<>();
    }

    int mid = (left + right) / 2;
    int midVal = arr[mid];

    if(findVal > midVal) {
        return binarySearch2(arr, mid + 1, right, findVal);
    } else if(findVal < midVal) {
        return binarySearch2(arr, left, mid - 1, findVal);
    } else {
        List<Integer> list = new ArrayList<>();
        int temp = mid - 1;
        while(true) {
            if(temp < 0 || arr[temp] != findVal) {
                break;
            }
            list.add(temp);
            temp--;
        }

        list.add(mid);

        temp = mid + 1;
        while(true) {
            if(temp > arr.length - 1 || arr[temp] != findVal) {
                break;
            }
            list.add(temp);
            temp++;
        }

        return list;
    }
}
```

