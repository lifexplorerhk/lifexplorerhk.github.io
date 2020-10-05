---
title: Array Queue
date: 2020-06-15 20:29:13
tags: Data Structure
---

Array Queue

```java
public ArrayQueue(int maxSize) {
    this.maxSize = maxSize;
    arr = new int[maxSize];
    front = -1; //指向隊列頭一個數據的前一個位置
    rear = -1; //指向隊列最後一個數據
}

public boolean isFull() {
    return rear == maxSize - 1;
}

public boolean isEmpty() {
    return front == rear;
}
```