---
title: Calculator
date: 2020-06-25 20:15:39
tags: Data Structure
---

Calculator

```java
ArrayStack numStack = new ArrayStack(10);
ArrayStack operStack = new ArrayStack(10);

int index = 0;
int num1 = 0;
int num2 = 0;
int oper = 0;
int res = 0;
char ch = ' ';
String keepNum = "";

while(true) {
    ch = expression.substring(index, index+1).charAt(0);
    if(operStack.isOper(ch)) {
        if(operStack.isEmpty()) {
            operStack.push(ch);
        } else {
            if(operStack.priority(ch) <= operStack.priority(operStack.peek())) {
                num1 = numStack.pop();
                num2 = numStack.pop();
                oper = operStack.pop();
                res = numStack.cal(num1, num2, oper);
                numStack.push(res);
                operStack.push(ch);
            } else {
                operStack.push(ch);
            }
        }
    } else {
        keepNum += ch;

        if(index == expression.length() - 1) {
            numStack.push(Integer.parseInt(keepNum));
        } else {
            if(operStack.isOper(expression.substring(index+1,index+2).charAt(0))) {
                numStack.push(Integer.parseInt(keepNum));
                keepNum = "";
            }
        }
    }
    index++;
    if(index == expression.length()) {
        break;
    }
}

while(true) {
    if(operStack.isEmpty()) {
        break;
    }
    num1 = numStack.pop();
    num2 = numStack.pop();
    oper = operStack.pop();
    res = numStack.cal(num1, num2, oper);
    numStack.push(res);
}

System.out.println(numStack.pop());
```

