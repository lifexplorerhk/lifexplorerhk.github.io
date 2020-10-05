---
title: Sparse Array
date: 2020-06-14 19:03:14
tags: Data Structure
---

Sparse Array 稀疏數組

```java
//遍歷chessArr，取得有效數據個數sum
int sum = 0;
for(int i=0; i<chessArr.length; i++) {
    for(int j=0; j<chessArr[0].length; j++) {
        if(chessArr[i][j] != null) {
            sum++;
        }
    }
}

Integer[][] sparseArr = new Integer[sum+1][3];
sparseArr[0][0] = chessArr.length;
sparseArr[0][1] = chessArr[0].length;
sparseArr[0][2] = sum;

//count代表當前發現的有效數據個數
int count = 0;
for(int i=0; i<chessArr.length; i++) {
    for(int j=0; j<chessArr[0].length; j++) {
        if(chessArr[i][j] != null) {
            count++;
            sparseArr[count][0] = i;
            sparseArr[count][1] = j;
            sparseArr[count][2] = chessArr[i][j];
        }
    }
}
```

