---
title: Josephus Problem
date: 2020-06-21 21:01:56
tags: Data Structure
---

Josephus Problem

```java
/*
start: 從第幾個node開始數數
count: 數幾下
num: 最初總共有幾個node
*/
public void count(int start, int count, int num) {
    if(head == null || start < 1 || count < 1 || start > num) {
        System.out.println("參數輸入有誤，請重新輸入");
        return;
    }
    Node helper = head;
    while(true) {
        if(helper.getNext() == head) { //helper指向最後一個節點
            break;
        }
        helper = helper.getNext();
    }
    //報數前，先讓head和helper移動 start - 1 次
    for (int i = 0; i < start - 1; i++) {
        head = head.getNext();
        helper = helper.getNext();
    }
    //報數時，讓head和helper移動 count -1 次，然後出圈
    //這裡是一個循環操作，直到圈中剩下一個節點
    while(true) {
        if(helper == head) {
            break;
        }
        for (int i = 0; i < count - 1; i++) {
            head = head.getNext();
            helper = helper.getNext();
        }
        //這時head指向要出圈的節點
        System.out.printf("節點編號%d出圈\n", head.getNo());
        head = head.getNext();
        helper.setNext(head);
    }
    System.out.println("最後留在圈中的節點編號是" + helper.getNo());
}
```

