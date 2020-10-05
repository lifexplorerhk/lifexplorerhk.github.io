---
title: Reverse Polish Notation Calculator
date: 2020-06-27 09:24:14
tags: Data Structure
---

Reverse Polish Notation Calculator

```java
public static List<String> getStringList(String postfixExpression) {
    String[] split = postfixExpression.split(" ");
    List<String> list = new ArrayList<>();
    for(String ele: split) {
        list.add(ele);
    }
    return list;
}

public static int calculate(List<String> list) {
    Stack<String> stack = new Stack<>();
    for(String str : list) {
        if(str.matches("\\d+")) { //匹配的是多位數
            stack.push(str);
        } else {
            int num2 = Integer.parseInt(stack.pop());
            int num1 = Integer.parseInt(stack.pop());
            int res = 0;
            if(str.equals("+")) {
                res = num1 + num2;
            } else if(str.equals("-")) {
                res = num1 - num2;
            } else if(str.equals("*")) {
                res = num1 * num2;
            } else if(str.equals("/")) {
                res = num1 / num2;
            } else {
                throw new RuntimeException("運算符有誤");
            }
            stack.push("" + res);
        }
    }
    return Integer.parseInt(stack.pop());
}

public static List<String> toInfixExpressionList(String expression) {
    List<String> list = new ArrayList<>();
    int i = 0;
    String str;
    char c;
    do {
        if((c = expression.charAt(i)) < 48 || (c = expression.charAt(i)) > 57) {
            list.add("" + c);
            i++;
        } else {
            str = "";
            while(i < expression.length() && (c = expression.charAt(i)) >= 48 && (c = expression.charAt(i)) <= 57) {
                str += c;
                i++;
            }
            list.add(str);
        }
    } while(i < expression.length());
    return list;
}

public static List<String> parsePostfixExpression(List<String> list) {
    Stack<String> stack = new Stack<>();
    List<String> postfixExpressionList = new ArrayList<>();

    for(String item: list) {
        if(item.matches("\\d+")) {
            postfixExpressionList.add(item);
        } else if(item.equals("(")) {
            stack.push(item);
        } else if(item.equals(")")) {
            while(!stack.peek().equals("(")) {
                postfixExpressionList.add(stack.pop());
            }
            stack.pop(); //將 ( 出棧
        } else {
            while(stack.size() != 0 && Operation.getValue(stack.peek()) >= Operation.getValue(item)) {
                postfixExpressionList.add(stack.pop());
            }
            stack.push(item);
        }
    }

    while(stack.size() != 0) {
        postfixExpressionList.add(stack.pop());
    }

    return postfixExpressionList;
}

static class Operation {
    private static int ADD = 1;
    private static int SUB = 1;
    private static int MUL = 2;
    private static int DIV = 2;

    public static int getValue(String operation) {
        int res = 0;
        switch(operation) {
            case "+":
                res = ADD;
                break;
            case "-":
                res = SUB;
                break;
            case "*":
                res = MUL;
                break;
            case "/":
                res = DIV;
                break;
            default:
                System.out.println("不存在該運算符");
                break;
        }
        return res;
    }
}
```

