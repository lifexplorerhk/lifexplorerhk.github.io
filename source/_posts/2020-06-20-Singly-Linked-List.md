---
title: Singly Linked List
date: 2020-06-20 09:12:34
tags: Data Structure
---

Singly Linked List

```java
//初始化一個頭節點，頭節點不要動，不存放具體數據
private HeroNode head = new HeroNode(0,"","");

//添加節點到Linked List
//不考慮編號順序
public void addNode(HeroNode node) {
    HeroNode temp = head;
    //遍歷Linked List，找到最後一個節點
    while(true) {
        if(temp.next == null) {
            break;
        }
        temp = temp.next;
    }
    //當退出while loop時，temp指向了Linked List最後一個節點
    temp.next = node;
}

//根據編號將英雄插入到指定位置
public void addNodeByOrder(HeroNode node) {
    //因為頭節點不能動，我們需要通過輔助指針(變量)來找到添加的位置
    //我們找的temp是位於添加位置的前一個節點，否則加入不了
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
        node.next = temp.next;
        temp.next = node;
    }
}

public void updateNode(HeroNode node) {
    if(head.next == null) {
        System.out.println("Linked list is empty.");
        return;
    }

    HeroNode temp = head.next;
    boolean flag = false; //標識是否找到準備編輯的英雄的編號
    while(true) {
        if(temp == null) {
            break;
        }
        if(temp.no == node.no) {
            flag = true;
            break;
        }
        temp = temp.next;
    }
    if(flag) {
        temp.name = node.name;
        temp.nickname = node.nickname;
    } else {
        System.out.printf("Cannot find hero with no=%d\n", node.no);
    }
}

public void deleteNode(int no) {
    if(head.next == null) {
        System.out.println("Linked list is empty.");
        return;
    }

    HeroNode temp = head;
    boolean flag = false;
    while(true) {
        if(temp.next == null) {
            break;
        }
        if(temp.next.no == no) {
            flag = true;
            break;
        }
        temp = temp.next;
    }
    if(flag) {
        temp.next = temp.next.next;
    } else {
        System.out.printf("Cannot delete hero with no=%d\n", no);
    }
}
```

總結：

什麼時候HeroNode temp = head，什麼時候HeroNode temp = head.next？

temp是一個指針，當你需要使用temp.next做事情，例如deleteNode()當中，temp需要指向head

```java
if(flag) {
    temp.next = temp.next.next;
}
```

如果你需要使用temp做事情，temp可以指向head.next，例如updateNode()當中

```java
if(flag) {
    temp.name = node.name;
    temp.nickname = node.nickname;
}
```

temp一開始指向哪裡，視乎你的解題思路，視乎你後面要做什麼。



Singly linked list的缺點

* 查找的方向只能是一個方向，向後查找，Doubly linked list可以向前或向後查找。
* Singly linked list不能自我刪除，需要靠輔助節點，總是通過temp，temp是待刪除節點的前一個節點；而Doubly linked list則可以自我刪除。