---
title: LeetCode中Dota2参议院题解
description: LeetCode中Dota2参议院题解-java
tags:
  - LeetCode
  - 算法
categories: LeetCode
abbrlink: 527a0a5e
date: 2020-12-11 10:23:00
---

#  LeetCode中Dota2参议院题解-java

## 题目

#### [649. Dota2 参议院](https://leetcode-cn.com/problems/dota2-senate/)

难度中等126

Dota2 的世界里有两个阵营：`Radiant`(天辉)和 `Dire`(夜魇)

Dota2 参议院由来自两派的参议员组成。现在参议院希望对一个 Dota2 游戏里的改变作出决定。他们以一个基于轮为过程的投票进行。在每一轮中，每一位参议员都可以行使两项权利中的`**一**`项：

1. `禁止一名参议员的权利`：

   参议员可以让另一位参议员在这一轮和随后的几轮中丧失**所有的权利**。

2. `宣布胜利`：

​     如果参议员发现有权利投票的参议员都是**同一个阵营的**，他可以宣布胜利并决定在游戏中的有关变化。

 

给定一个字符串代表每个参议员的阵营。字母 “R” 和 “D” 分别代表了 `Radiant`（天辉）和 `Dire`（夜魇）。然后，如果有 `n` 个参议员，给定字符串的大小将是 `n`。

以轮为基础的过程从给定顺序的第一个参议员开始到最后一个参议员结束。这一过程将持续到投票结束。所有失去权利的参议员将在过程中被跳过。

假设每一位参议员都足够聪明，会为自己的政党做出最好的策略，你需要预测哪一方最终会宣布胜利并在 Dota2 游戏中决定改变。输出应该是 `Radiant` 或 `Dire`。

 

**示例 1：**

```
输入："RD"
输出："Radiant"
解释：第一个参议员来自 Radiant 阵营并且他可以使用第一项权利让第二个参议员失去权力，因此第二个参议员将被跳过因为他没有任何权利。然后在第二轮的时候，第一个参议员可以宣布胜利，因为他是唯一一个有投票权的人
```

**示例 2：**

```
输入："RDD"
输出："Dire"
解释：
第一轮中,第一个来自 Radiant 阵营的参议员可以使用第一项权利禁止第二个参议员的权利
第二个来自 Dire 阵营的参议员会被跳过因为他的权利被禁止
第三个来自 Dire 阵营的参议员可以使用他的第一项权利禁止第一个参议员的权利
因此在第二轮只剩下第三个参议员拥有投票的权利,于是他可以宣布胜利
```

 

**提示：**

- 给定字符串的长度在 `[1, 10,000]` 之间.

## 题解

### 方法一：双队列

#### 思路

用两个队列，遍历字符串，将两个阵营的下标放在两个队列中，然后遍历这两个队列，每次取出一个，判断其大小，若R<D则将R的下标+字符串长度重新放入队列中，最后不为空的队列即为获胜。

#### 代码实现

```java
class Solution {
    public String predictPartyVictory(String senate) {
        int n = senate.length();
        Queue<Integer> radiantQueue = new LinkedList<Integer>();
        Queue<Integer> direQueue    = new LinkedList<Integer>();

        // 1. 遍历数组 记录下每个阵营议员的下标
        for(int i = 0;i < n;i++){
            if(senate.charAt(i) == 'R'){
                radiantQueue.offer(i);
            }else{
                direQueue.offer(i);
            }
        }

        // 2. 如果两个队列都不空的情况下
        while(!radiant.isEmpty() && !dire.isEmpty()){
            int radiantIndex = radiant.poll();      // radiant的第一名议员弹出
            int direIndex    = dire.poll();         // dire 的第一名议员弹出
            if(radiantIndex < direIndex){           // 如果radiant第一名议员首元素较小
                radiantQueue.offer(radiantIndex + n);    //+n之后重新放回队列 对应dire第一名议员永久弹出
            }else{
                direQueue.offer(direIndex + n);          //+n之后重新放回队列 对应radiant第一名议员永久弹出
            }
        }
        // 3. 宣布胜利
        return !radiant.isEmpty()?"Radiant":"Dire"; // 最后非空的队列宣布胜利
    }
}
```



#### 复杂度分析

- 时间复杂度：O(n)，其中 n 是字符串 senate 的长度。在模拟整个投票过程的每一步，我们进行的操作的时间复杂度均为 O(1)，并且会弹出一名天辉方或夜魇方的议员。由于议员的数量为 n，因此模拟的步数不会超过 n，时间复杂度即为 O(n)。


- 空间复杂度：O(n)，即为两个队列需要使用的空间。




#### 提交详情

![image-20201211103841323](https://gitee.com/happyzm/images/raw/master/image-20201211103841323.png)

### 方法二：

#### 思路



#### 代码实现



#### 复杂度分析



#### 提交详情