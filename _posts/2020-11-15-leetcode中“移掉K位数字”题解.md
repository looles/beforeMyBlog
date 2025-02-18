﻿---
layout: post
title: "LeetCode中移掉K位数字题解"
date: 2020-11-15 
description: "LeetCode刷题"
tag: LeetCode
---

## 题目
402. 移掉K位数字
给定一个以字符串表示的非负整数 num，移除这个数中的 k 位数字，使得剩下的数字最小。

注意:

```java
num 的长度小于 10002 且 ≥ k。
num 不会包含任何前导零。
```

示例 1 :

```java
输入: num = "1432219", k = 3
输出: "1219"
解释: 移除掉三个数字 4, 3, 和 2 形成一个新的最小的数字 1219。
```

示例 2 :

```java
输入: num = "10200", k = 1
输出: "200"
解释: 移掉首位的 1 剩下的数字为 200. 注意输出不能有任何前导零。
```

示例 3 :

```java
输入: num = "10", k = 2
输出: "0"
解释: 从原数字移除所有的数字，剩余为空就是0。
```

## 题解
解释：
给定一个长度为 nn 的数字序列 [D0D1D2D3···Dn-1]，从左往右找到第一个位置 i（i>0）使得 Di<Di-1，删去 Di-1；如果不存在，说明整个数字序列单调不降，删去最后一个数字即可。

基于此，我们可以每次对整个数字序列执行一次这个策略；删去一个字符后，剩下的 n−1 长度的数字序列就形成了新的子问题，可以继续使用同样的策略，直至删除 k 次。

方法一：
思路：从左到右，找到第一个比后面大的字符，删除这个字符，k次扫描

```java
class Solution {
    public String removeKdigits(String num, int k) {
        if (num.length() == k) return "0";  //如果字符长度等于k，则直接返回0
        StringBuilder s = new StringBuilder(num);
        for (int i = 0; i < k; i++) {       // K次扫描
            int idx = 0;
            for (int j = 1; j < s.length() && s.charAt(j) >= s.charAt(j - 1); j++) idx = j;             //定位到第一个比后面大的字符
            s.delete(idx, idx + 1);       //删除这个字符
            //如果此时的字符长度大于1并且第一个字符为0时，则删除第一个字符
            while (s.length() > 1 && s.charAt(0) == '0'){
                s.delete(0, 1);
            } 
        }
        return s.toString();
    }
}
```

