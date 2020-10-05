---
title: Eight Queens
date: 2020-06-29 22:21:57
tags: Algorithm
---

Eight Queens

```java
private void check(int n) {
    if(n == max) { //n從0開始，n==8代表正在放第9個皇后，也說明前面8個皇后已經擺放好
        print();
        return;
    }

    //依次擺放皇后，並判斷是否有衝突
    for (int i = 0; i < max; i++) {
        arr[n] = i; //每次將皇后擺放在下一列，然後judge
        if(judge(n)) { //不衝突
            //放n+1個皇后
            check(n + 1);
        }
    }
}

//查看當我們放第n個皇后時，檢測該皇后是否和前面已經擺放的皇后衝突
private boolean judge(int n) {
    judgeCount++;
    for (int i = 0; i < n; i++) {
        // arr[i] == arr[n] 代表第n個皇后和前面已經擺放的皇后在同一列
        // Math.abs(n-i) == Math.abs(arr[n] - arr[i]) 代表第n個皇后和前面已經擺放的皇后在同一斜線
        if(arr[i] == arr[n] || Math.abs(n-i) == Math.abs(arr[n] - arr[i])) {
            return false; //代表有衝突
        }
    }
    return true; //沒衝突
}
```

