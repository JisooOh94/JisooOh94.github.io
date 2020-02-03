---
title: "[LeetCode] 8. String to Integer"
permalink: /algorithm/String_to_integer
excerpt: "Time Complexity : O(n)"
classes: wide
categories:
  - Algorithm
tags:
  - Algorithm
  - LeetCode
---
* Time Complexity : O(n)
* Trial Count : 1
* Result : Success
* Performace
   * Time : 3ms, 30.84%
   * Memory : 40mb, 5.59%
   
```java
public int myAtoi(String str) {
    if(str == null) {
        return 0;
    }

    boolean isStart = false;
    long num = 0;
    int sign = 1;

    for(int i = 0; i < str.length()s; i++) {
        char word = str.charAt(i);
        if(isStart) {
            if('0' <= word && word <= '9') {
                num = num * 10 + (word - 48);

                if(sign == 1 && num >= INT_MAX) {
                    return INT_MAX;
                } else if(sign == -1 && num * sign <= INT_MIN) {
                    return INT_MIN;
                }
            } else {
                break;
            }
        } else {
            if(word == ' ') {
                continue;
            } else if(word == '+' || word == '-') {
                if(word == '-') {
                    sign = -1;
                }
                isStart = true;
            } else if('0' <= word && word <= '9') {
                num = word - 48;
                isStart = true;
            } else {
                return 0;
            }
        }
    }

    return (int)num * sign;
}
```