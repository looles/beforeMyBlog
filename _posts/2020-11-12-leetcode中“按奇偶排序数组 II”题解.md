## 题目
922. 按奇偶排序数组 II
给定一个非负整数数组 A， A 中一半整数是奇数，一半整数是偶数。

对数组进行排序，以便当 A[i] 为奇数时，i 也是奇数；当 A[i] 为偶数时， i 也是偶数。

你可以返回任何满足上述条件的数组作为答案。

 

示例：

输入：[4,2,5,7]
输出：[4,5,2,7]
解释：[4,7,2,5]，[2,5,4,7]，[2,7,4,5] 也会被接受。
 

提示：

2 <= A.length <= 20000
A.length % 2 == 0
0 <= A[i] <= 1000

## 题解
1、遍历法
新建一个数组result用来存储排序后的数组，使用变量ji和ou来代表result数组的下标，然后用下标i遍历原数组，若A[i]为奇数，将A[i]存入result[ji]，并将ji加2，若A[i]为偶数。将A[i]存入result[ou]，并将ou加2，遍历完成后，所有的数据均正确放入数组result中

```java
class Solution {
    public int[] sortArrayByParityII(int[] A) {
        int[] result = new int[A.length];       //用来存储排序后的数组
        int ji = 1;                            //用来表示奇数值的下标
        int ou = 0;                            //用来表示偶数值的下标
        for(int i = 0; i < A.length; i++){      //遍历原数组
            if(A[i] % 2 == 0){                  //如此为偶数，将此时值赋予result[ou]，并将偶数下标加2
                result[ou] = A[i];
                ou += 2;
            }else{
                result[ji] = A[i];              //若为奇数，将此时值赋予result[ji]， 并将奇数下标加2
                ji += 2;
            }
        }

        return result;
    }
}
```
复杂度分析

时间复杂度：O(N)O(N)，其中 NN 是数组 A 的长度。

空间复杂度：O(1)O(1)。注意在这里我们不考虑输出数组的空间占用。

2、使用双指针在原数组修改
使用i和 j来分别维护数组的偶数下标与奇数下标，如果A[i]为奇数，并且此时A[j]为奇数，将j 移两个单位，直到遇到下一个偶数（A[j]为偶数），此时，直接将A[i]与A[j]交换，不断执行这样的过程，最后将所有的整数放在正确的位置。

```java
class Solution{
    public int[] sortArrayByParityII(int[] A) {
        int n = A.length;       
        int i = 0;              //i 用来数组中偶数下标的值
        int j = 1;              //j 用来表示数组中奇数下标的值
        for(i = 0; i < n; i += 2){      //遍历数组中偶数下标的值
            if(A[i] % 2 == 1){          //如偶数下标的值为奇数
                while(A[j] % 2 == 1){   //遍历奇数下标的值，若为奇数，j加2，否则，将下标i与下标j的值交换
                    j += 2;
                }
                swap(A,i,j);
            }
        }
        return A;
    }

    private void swap(int[] array, int i, int j){
        int temp = array[i];
        array[i] = array[j];
        array[j] = temp;
    }
}
```
复杂度分析

时间复杂度：O(N)O(N)，其中 NN 是数组 A 的长度。

空间复杂度：O(1)O(1)。
