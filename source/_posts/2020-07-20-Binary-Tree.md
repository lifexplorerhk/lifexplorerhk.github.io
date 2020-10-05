---
title: Binary Tree
date: 2020-07-20 21:07:49
tags: Data Structure
---

Binary Tree

```java
public void delNode(int no) {
    if(this.left != null && this.left.no == no) {
        this.left = null;
        return;
    }
    if(this.right != null && this.right.no == no) {
        this.right = null;
        return;
    }
    if(this.left != null) {
        this.left.delNode(no);
    }
    if(this.right != null) {
        this.right.delNode(no);
    }
}

public void preOrder() {
    System.out.println(this);
    if(this.left != null) {
        this.left.preOrder();
    }
    if(this.right != null) {
        this.right.preOrder();
    }
}

public void infixOrder() {
    if(this.left != null) {
        this.left.infixOrder();
    }
    System.out.println(this);
    if(this.right != null) {
        this.right.infixOrder();
    }
}

public void postOrder() {
    if(this.left != null) {
        this.left.postOrder();
    }
    if(this.right != null) {
        this.right.postOrder();
    }
    System.out.println(this);
}

public HeroNode preOrderSearch(int no) {
    if(this.no == no) {
        return this;
    }
    HeroNode resNode = null;
    if(this.left != null) {
        resNode = this.left.preOrderSearch(no);
    }
    if(resNode != null) {
        return resNode;
    }
    if(this.right != null) {
        resNode = this.right.preOrderSearch(no);
    }
    return resNode;
}

public HeroNode infixOrderSearch(int no) {
    HeroNode resNode = null;
    if(this.left != null) {
        resNode = this.left.infixOrderSearch(no);
    }
    if(resNode != null) {
        return resNode;
    }
    if(this.no == no) {
        return this;
    }
    if(this.right != null) {
        resNode = this.right.infixOrderSearch(no);
    }
    return resNode;
}

public HeroNode postOrderSearch(int no) {
    HeroNode resNode = null;
    if(this.left != null) {
        resNode = this.left.postOrderSearch(no);
    }
    if(resNode != null) {
        return resNode;
    }
    if(this.right != null) {
        resNode = this.right.postOrderSearch(no);
    }
    if(resNode != null) {
        return resNode;
    }
    if(this.no == no) {
        return this;
    }
    return resNode;
}
```

