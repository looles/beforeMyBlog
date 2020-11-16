---
layout: post
title: "LeetCode中最接近原点的k个点题解"
date: 2020-11-09 
description: "LeetCode刷题"
tag: LeetCode
---

## 题目
973. 最接近原点的 K 个点
我们有一个由平面上的点组成的列表 points。需要从中找出 K 个距离原点 (0, 0) 最近的点。

（这里，平面上两点之间的距离是欧几里德距离。）

你可以按任何顺序返回答案。除了点坐标的顺序之外，答案确保是唯一的。

 

示例 1：

输入：points = [[1,3],[-2,2]], K = 1
输出：[[-2,2]]
解释： 
(1, 3) 和原点之间的距离为 sqrt(10)，
(-2, 2) 和原点之间的距离为 sqrt(8)，
由于 sqrt(8) < sqrt(10)，(-2, 2) 离原点更近。
我们只需要距离原点最近的 K = 1 个点，所以答案就是 [[-2,2]]。
示例 2：

输入：points = [[3,3],[5,-1],[-2,4]], K = 2
输出：[[3,3],[-2,4]]
（答案 [[-2,4],[3,3]] 也会被接受。）
 

提示：

1 <= K <= points.length <= 10000
-10000 < points[i][0] < 10000
-10000 < points[i][1] < 10000

## 题解
方法一：排序
将每个点到原点的欧几里得距离的平方从小到大排序后，取出前K个即可。

```java
class Solution {
    public int[][] kClosest(int[][] points, int K) {
        Arrays.sort(points, new Comparator<int[]>() {
            public int compare(int[] point1, int[] point2) {
                return (point1[0] * point1[0] + point1[1] * point1[1]) - (point2[0] * point2[0] + point2[1] * point2[1]);
            }
        });
        return Arrays.copyOfRange(points, 0, K);
    }
}
```

复杂度分析：
时间复杂度：O(nlogn）
空间复杂度：O(logn）

方法二：优先队列
使用一个优先队列实时维护前K个最小的距离平方。
首先我们将前 KK 个点的编号（为了方便最后直接得到答案）以及对应的距离平方放入优先队列中，随后从第 K+1K+1 个点开始遍历：如果当前点的距离平方比堆顶的点的距离平方要小，就把堆顶的点弹出，再插入当前的点。当遍历完成后，所有在优先队列中的点就是前 KK 个距离最小的点。

```java
class Solution {
    public int[][] kClosest(int[][] points, int K) {
        //方法一：排序
        // Arrays.sort(points, new Comparator<int[]>(){
        //     public int compare(int[] point1,int[] point2){
        //         return (point1[0] * point1[0] + point1[1] * point1[1]) - (point2[0] * point2[0] + point2[1] * point2[1]);
        //     }
        // });
        // return Arrays.copyOfRange(points, 0, K);
    
        //方法二：优先队列
        PriorityQueue<int[]> pq = new PriorityQueue<int[]>(new Comparator<int[]>(){
            public int compare(int[] array1,int[] array2){
                return array2[0] - array1[0];
            }
        });
        for(int i = 0; i < K; ++i){
            pq.offer(new int[]{points[i][0] * points[i][0] + points[i][1] * points[i][1], i});
        }
        int n = points.length;
        for(int i = K; i < n; ++i){
            int dist = points[i][0] * points[i][0] + points[i][1] * points[i][1];
            if(dist < pq.peek()[0]){
                pq.poll();
                pq.offer(new int[]{dist, i});

            }
        }
        int[][] ans = new int[K][2];
        for(int i = 0; i < K; ++i){
            ans[i] = points[pq.poll()[1]];
        }
        return ans;
    }
}
```
复杂度分析：
时间复杂度：O(nlogK）
空间复杂度：O(K)

