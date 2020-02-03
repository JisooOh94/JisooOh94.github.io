---
title: "[LeetCode] 5. Longest Palindromic Substring"
permalink: /algorithm/Longest_Palindromic_Substring
excerpt: "Time Complexity : O(n^2)"
classes: wide
categories:
  - Algorithm
tags:
  - Algorithm
  - LeetCode
---
* Time Complexity : O(n^2)
* Trial Count : 6
* Result : Success
* Performace
   * Time : 18.10
   * Memory : 7.26
   
```java
public static String longestPalindrome(String sample) {
    if(sample == null || sample.length() > 1000) {
		return null;
	} else if(sample.length() <= 1) {
		return sample;
	}

	String pelindrome = "";
	for(int forwardIdx = 0; forwardIdx <= sample.length() - pelindrome.length() - 1; forwardIdx++) {
		for(int backwardIdx = sample.length() - 1; pelindrome.length() + forwardIdx <= backwardIdx; backwardIdx--) {
			int length = (backwardIdx - forwardIdx + 1);
			int mid = forwardIdx + length/2;

			boolean isPelindrome = true;
			for(int innerIdx = 0; forwardIdx + innerIdx < mid; innerIdx++) {
				if(sample.charAt(forwardIdx + innerIdx) != sample.charAt(backwardIdx - innerIdx)) {
					isPelindrome = false;
					break;
				}
			}

			if(isPelindrome) {
				pelindrome = sample.substring(forwardIdx, backwardIdx + 1);
				break;
			}
		}
	}

	return pelindrome;
}
```