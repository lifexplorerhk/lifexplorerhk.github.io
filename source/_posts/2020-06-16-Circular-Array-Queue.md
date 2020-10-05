---
title: Circular Array Queue
date: 2020-06-16 22:33:35
tags: Data Structure
---

Circular Array Queue

```java
private int maxSize;
private int front; //指向隊列第一個元素，初始值是0
private int rear; //指向隊列最後一個元素的後一個位置，初始值是0，arr[rear]總是一個空白位置
private int[] arr;

public boolean isFull() {
    // 假設maxSize=4，當rear=3，front=0，隊列已滿
    // 假設maxSize=4，當rear=0，front=1，隊列已滿
    return (rear + 1) % maxSize == front;
}

public boolean isEmpty() {
    return front == rear;
}

public void addToQueue(int num) {
    if(isFull()) {
        System.out.println("The queue is full, cannot add data.");
        return;
    }
    arr[rear] = num;
    rear = (rear + 1) % maxSize;
}

public int getFrmQueue() {
    if(isEmpty()) {
        throw new RuntimeException("The queue is empty, cannot retrieve 			data.");
    }
    int value = arr[front];
    front = (front + 1) % maxSize;
    return value;
}

public void showQueue() {
    if(isEmpty()) {
        System.out.println("The queue is empty, there are no data.");
        return;
    }
    for (int i = front; i < front + size(); i++) {
        System.out.printf("arr[%d]=%d\n", i % maxSize, arr[i % maxSize]);
    }
}

public int peekQueue() {
    if(isEmpty()) {
        throw new RuntimeException("The queue is empty, there are no data.");
    }
    return arr[front];
}

//求得當前有效數據的個數
public int size() {
    // 假設maxSize=4，rear=1，front=0，有效數據1個
    // 假設maxSize=4，rear=3，front=1，有效數據2個
    return (rear + maxSize - front) % maxSize;
}
```
