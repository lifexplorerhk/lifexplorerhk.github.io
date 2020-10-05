---
title: Hash Table
date: 2020-07-15 16:19:17
tags: Data Structure
---

Hash Table

```java
static class Emp {
    public int id;
    public String name;
    public Emp next;

    public Emp(int id, String name) {
        this.id = id;
        this.name = name;
    }
}

static class EmpLinkedList {
    private Emp head;

    public void add(Emp emp) {
        if(head == null) {
            head = emp;
            return;
        }
        Emp temp = head;
        while(temp.next != null) {
            temp = temp.next;
        }
        temp.next = emp;
    }

    public void del(int id) {
        if(head == null) {
            System.out.printf("id %d not found.\n", id);
            return;
        }
        if(head.id == id) {
            head = head.next;
            System.out.printf("Employee id=%d is deleted.\n", id);
            return;
        }
        if(head.next == null) {
            System.out.printf("id %d not found.\n", id);
            return;
        }
        Emp temp = head;
        Emp cur = temp.next;
        while(cur.id != id) {
            if(cur.next == null) {
                System.out.printf("id %d not found.\n", id);
                return;
            }
            cur = cur.next;
            temp = temp.next;
        }
        temp.next = cur.next;
        System.out.printf("Employee id=%d is deleted.\n", id);
    }

    public void list(int no) {
        if(head == null) {
            System.out.println("Linked List " + (no + 1) +" is empty.");
            return;
        }
        System.out.print("Linked List " + (no + 1) +" as follow:");
        Emp temp = head;
        while(temp != null) {
            System.out.printf(" => id=%d name=%s\t", temp.id, temp.name);
            temp = temp.next;
        }
        System.out.println();
    }

    public Emp findEmpById(int id) {
        if(head == null) {
            System.out.println("Linked List is empty.");
            return null;
        }
        Emp temp = head;
        while(temp.id != id) {
            if(temp.next == null) {
                break;
            }
            temp = temp.next;
        }
        return temp.id == id ? temp : null;
    }
}
```

