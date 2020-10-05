---
title: Array Stack
date: 2020-06-23 21:05:31
tags: Data Structure
---

Array Stack

```java
private int maxSize;
private int[] stack;
private int top = -1;

public ArrayStack(int maxSize) {
    this.maxSize = maxSize;
    stack = new int[this.maxSize];
}

public void push(int num) {
    if(isFull()) {
        System.out.println("棧滿");
        return;
    }
    top++;
    stack[top] = num;
}

public int pop() {
    if(isEmpty()) {
        throw new RuntimeException("棧空");
    }
    int temp = stack[top];
    top--;
    return temp;
}

public void list() {
    if(isEmpty()) {
        System.out.println("棧空");
        return;
    }
    //從棧頂開始顯示數據
    for (int i = top; i >= 0 ; i--) {
        System.out.printf("stack[%d]=%d\n", i, stack[i]);
    }
}
```

