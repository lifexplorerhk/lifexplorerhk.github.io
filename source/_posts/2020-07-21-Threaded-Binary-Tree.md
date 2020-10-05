---
title: Threaded Binary Tree
date: 2020-07-21 22:27:12
tags: Data Structure
---

Threaded Binary Tree

```java
static class HeroNode {
    private int no;
    private String name;
    private HeroNode left;
    private HeroNode right;
    private int leftType; //0:指向左子樹，1:指向前驅節點
    private int rightType; //0:指向右子樹，1:指向後繼節點
}

public void threadedNode(HeroNode node) {
    if(node == null) {
        return;
    }

    threadedNode(node.left);

    if(node.left == null) {
        node.left = pre;
        node.leftType = 1;
    }
    if(pre != null && pre.right == null) {
        pre.right = node;
        pre.rightType = 1;
    }
    pre = node;

    threadedNode(node.right);
}

public void threadedList() {
    HeroNode node = root;
    while(node != null) {
        while(node.leftType == 0) {
            node = node.left;
        }
        System.out.println(node);
        while(node.rightType == 1) {
            node = node.right;
            System.out.println(node);
        }

        node = node.right;
    }
}
```

