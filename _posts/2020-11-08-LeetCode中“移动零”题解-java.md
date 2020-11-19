---
layout: post
title: "LeetCode中移动零题解"
date: 2020-11-08
description: "LeetCode刷题"
tag: LeetCode
---

## 题目
283. 移动零
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

示例:

输入: [0,1,0,3,12]
输出: [1,3,12,0,0]
说明:

必须在原数组上操作，不能拷贝额外的数组。
尽量减少操作次数。

## 题解
1、双指针
创建两个指针i和j，第一次遍历时，用指针j用来记录有多少非0元素，在每次遇到一个非0元素就将其往数组左边挪，j指针的下标指向了最后一个非0元素下标，第二次遍历时，起始位置从j开始，将剩下的元素全部置为0。

```java
class Solution {
	public void moveZeroes(int[] nums) {
		if(nums==null) {
			return;
		}
		//第一次遍历的时候，j指针记录非0的个数，只要是非0的统统都赋给nums[j]
		int j = 0;
		for(int i=0;i<nums.length;++i) {
			if(nums[i]!=0) {
				nums[j++] = nums[i];
			}
		}
		//非0元素统计完了，剩下的都是0了
		//所以第二次遍历把末尾的元素都赋为0即可
		for(int i=j;i<nums.length;++i) {
			nums[i] = 0;
		}
	}
}	
```

2、快速排序
确定一个待分割的元素做中间点x,然后把所有小于等于x的元素放到x的左边，大于x的元素放到右边。
在此题中，用0当做这个中间点，把不等于0的放到中间点的左边（没说不能为负数，所以此处条件为不等于0），等于0的放到其右边。

```java	
class Solution {
    public void moveZeroes(int[] nums) {
    	//两个指针i和j
        int i = 0, j = 0;
        if(nums == null) return;
        for(i=0; i < nums.length; i++){
        //当前元素!=0，就把其交换到左边，等于0的交换到右边
            if(nums[i] != 0){
                int temp = nums[i];
                nums[i] = nums[j];
                nums[j] = temp;
                j++;
            }
        }
    }
}
```

