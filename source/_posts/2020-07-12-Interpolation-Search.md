---
title: Interpolation Search
date: 2020-07-12 11:11:38
tags: Algorithm
---

Interpolation Search

```java
public static List<Integer> interpolationSearch(int[] arr, int left, int right, int findVal) {
    if(left > right || findVal < arr[0] || findVal > arr[arr.length - 1]) {
        return new ArrayList<>();
    }

    int mid = left + (right - left) * (findVal - arr[left]) / (arr[right] - arr[left]);
    int midVal = arr[mid];

    if(findVal > midVal) {
        return interpolationSearch(arr, mid + 1, right, findVal);
    } else if(findVal < midVal) {
        return interpolationSearch(arr, left, mid - 1, findVal);
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

