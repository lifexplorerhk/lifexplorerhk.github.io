---
title: Singly Linked List Interview Question
date: 2020-06-20 10:54:57
tags: Data Structure
---

Singly Linked List Interview Question

```java
//獲取Linked list中節點的個數，不統計頭節點
public static int getLength(HeroNode head) {
    if(head.next == null) {
        return 0;
    }
    int length = 0;
    HeroNode temp = head.next;
    while(temp != null) {
        length++;
        temp = temp.next;
    }
    return length;
}

//獲取Linked list中倒數第k個節點
public static HeroNode getLastIndexNode(HeroNode head, int index) {
    if(head.next == null) {
        return null;
    }
    int length = getLength(head);
    if(index <=0 || index > length) {
        return null;
    }
    HeroNode temp = head.next;
    for (int i = 0; i < length - index; i++) {
        temp = temp.next;
    }
    return temp;
}

//反轉Linked list
public static void reverseList(HeroNode head) {
    if(head.next == null || head.next.next == null) {
        return;
    }

    HeroNode cur = head.next;
    HeroNode next = null;
    HeroNode reverseHead = new HeroNode(0,"","");
    while(cur != null) {
        next = cur.next; //利用next保存下一個節點
        cur.next = reverseHead.next; //將cur的下一個節點指向新Linked list的最前端
        reverseHead.next = cur; //將當前節點cur連接到新Linked list
        cur = next; //cur後移
    }
    head.next = reverseHead.next;
}

//逆序打印Linked list
public static void reversePrint(HeroNode head) {
    if(head.next == null) {
        return;
    }
    Stack<HeroNode> stack = new Stack<>();
    HeroNode temp = head.next;
    while(temp != null) {
        stack.push(temp);
        temp = temp.next;
    }
    while(stack.size() > 0) {
        System.out.println(stack.pop());
    }
}
```

