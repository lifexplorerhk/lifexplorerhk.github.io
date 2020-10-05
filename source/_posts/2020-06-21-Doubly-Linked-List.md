---
title: Doubly Linked List
date: 2020-06-21 13:47:12
tags: Data Structure
---

Doubly Linked List

```java
public void addNodeByOrder(HeroNode node) {
    //因為頭節點不能動，我們需要通過輔助指針(變量)來找到添加的位置
    //我們找的temp是位於添加位置的前一個節點
    HeroNode temp = head;
    boolean flag = false; //標識添加的編號是否存在
    while(true) {
        if(temp.next == null) {
            break;
        }
        if(temp.next.no > node.no) {
            break;
        } else if (temp.next.no == node.no) {
            flag = true;
            break;
        }
        temp = temp.next;
    }
    //退出while loop
    if(flag) {
        System.out.printf("準備加入的英雄的編號 %d 已經存在，不能加入\n", node.no);
    } else {
        if(temp.next == null) {
            node.prev = temp;
            temp.next = node;
        } else {
            node.prev = temp;
            node.next = temp.next;
            temp.next.prev = node;
            temp.next = node;
        }
    }
}
```

