---
title: Singly Linked List Stack
date: 2020-06-23 21:08:54
tags: Data Structure
---

Singly Linked List Stack

```java
private Node head = new Node(0);

public void push(int num) {
    Node node = new Node(num);
    Node temp = head;
    while(temp.next != null) {
        temp = temp.next;
    }
    temp.next = node;
}

public int pop() {
    if(head.next == null) {
        throw new RuntimeException("棧空");
    }
    Node temp = head;
    while(temp.next.next != null) {
        temp = temp.next;
    }
    int val = temp.next.num;
    temp.next = null;
    return val;
}

public void list() {
    if(head.next == null) {
        System.out.println("棧空");
        return;
    }
    Stack<Node> stack = new Stack<>();
    Node temp = head.next;
    while(temp != null) {
        stack.push(temp);
        temp = temp.next;
    }
    while(stack.size() > 0) {
        System.out.println(stack.pop());
    }
}
```

