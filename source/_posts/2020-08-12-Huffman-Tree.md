---
title: Huffman Tree
date: 2020-08-12 21:04:24
tags: Data Structure
---

Huffman Tree

~~~java
public static Node createHuffmanTree(int[] arr) {
    List<Node> nodeList = new ArrayList<>();
    for(int value : arr) {
        nodeList.add(new Node(value));
    }

    while(nodeList.size() > 1) {
        Collections.sort(nodeList);

        Node left = nodeList.get(0);
        Node right = nodeList.get(1);

        Node parent = new Node(left.value + right.value);
        parent.left = left;
        parent.right = right;

        nodeList.remove(left);
        nodeList.remove(right);

        nodeList.add(parent);
    }

    return nodeList.get(0);
}

@Override
public int compareTo(Node o) {
    //從小到大排序
    //如果想從大到小排序，則寫成 -(this.value - o.value)
    return this.value - o.value;
}
~~~
