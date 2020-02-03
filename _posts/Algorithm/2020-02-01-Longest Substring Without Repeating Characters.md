---
title: "[LeetCode] 3. Longest Substring Without Repeating Characters"
permalink: /algorithm/Longest_Substring_Without_Repeating_Characters
excerpt: 빌더패턴과 Json Serialization 연동하는 방법 및 효율적으로 활용하는 방법에 대해 기술
classes: wide
categories:
  - Algorithm
tags:
  - Algorithm
  - LeetCode
---
[LeetCode] 3. Longest Substring Without Repeating Characters

* Time Complexity : O(n)
* Trial Count : 1
* Result : Success
```java
public int lengthOfLongestSubstring(String sampleStr) {
		if(sampleStr == null || sampleStr == "") {
			return 0;
		}

		int maxSize = 0;
		long strLength = sampleStr.length();
		Map<Character, Integer> map = new HashMap<Character, Integer>((int)strLength);

		long startIdx = 0;
		long lastIdx = 0;

		for(long i = 0; i< strLength; i++) {
			char curChar = sampleStr.charAt((int)i);

			if(map.containsKey(curChar)) {
				int value = map.get(curChar);
				if(value >= startIdx) {
					startIdx = map.get(curChar) + 1;
				}
			}
			lastIdx++;
			map.put(curChar, (int)i);

			if(lastIdx - startIdx > maxSize) {
				maxSize = (int)(lastIdx - startIdx);
			}
		}

		return maxSize;
	}
```