---
title: "[LeetCode] 12. Integer to Roman"
permalink: /algorithm/Integer_To_Roman
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
* Performace
   * Time : 5ms, 49.35%
   * Memory : 40.9mb, 11.25%
   
```java
public String intToRoman(int num) {
    int rangeIdx = 0;
    int rangeNum[] = new int[]{1000, 900, 500, 400, 100, 90, 50, 40, 10, 9, 5, 4, 1};
    String rangeStr[] = new String[]{"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};

    String result = "";

    while(num != 0) {
        if(num - rangeNum[rangeIdx] >= 0) {
            num -= rangeNum[rangeIdx];
            result += rangeStr[rangeIdx];
        } else {
            rangeIdx++;
        }
    }
    return result;
}
```