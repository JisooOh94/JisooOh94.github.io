---
title: "[LeetCode] 11. Container With Most Water"
permalink: /algorithm/Container_With_Most_Water
excerpt: "Time Complexity : O(n^2)"
classes: wide
categories:
  - Algorithm
tags:
  - Algorithm
  - LeetCode
---
* Time Complexity : O(n^2)
* Trial Count : 1
* Result : Success
* Performace
   * Time : 179ms, 24.77%
   * Memory : 41.4mb, 5.77%
   
```java
public int maxArea(int[] height) {
    int maxArea = 0;
    for(int i = 0; i < height.length; i++) {
        int forwardIdx = height.length - 1;
        while(forwardIdx > i) {
            if(height[forwardIdx] >= height[i]) {
                int area = height[i] * (forwardIdx - i);
                if(area > maxArea) {
                    maxArea = area;
                }
                break;
            }
            forwardIdx--;
       }

        int backIdx = height.length -1 -i;
        int backwardIdx = 0;
        while(backwardIdx < backIdx) {
            if(height[backwardIdx] >= height[backIdx]) {
                int area = height[backIdx] * (backIdx - backwardIdx);
                if(area > maxArea) {
                    maxArea = area;
                }
                break;
            }
            backwardIdx++;
        }
    }
    return maxArea;
}
```