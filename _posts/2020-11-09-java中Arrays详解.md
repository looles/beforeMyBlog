## Arrays类的定义
Arrays类在java.util包中，包含了操作数组的方法。

## 常用函数（静态）
1、Arrays.sort()
对数组按照升序排序
```java
int[] nums = {2, 4,6,7,3,8,1};
Arrays.sort(nums);
/*排序前：2 4 6 7 3 8 1
 *排序后：1 2 3 4 6 7 8
 */
```
Arrays.sort(Object[] array, int from, int to)
对数组元素指定范围进行排序（排序范围是从元素下标为from，到下标为to-1的元素）

```java
int[] nums = {2,5,0,4,1,-10};
        //对前四位元素进行排序
        Arrays.sort(nums, 0, 4);
        for(int i :nums)
            System.out.print(i+" ");
        /* 之前:2 5 0 4 1 -10
         * 结果:0 2 4 5 1 -10 
         */
```

2、Arrays.fill(Object[] array, Object object)
为数组元素填充相同的值

```java
int[] nums = {2,5,0,4,1,-10};
        Arrays.fill(nums, 1);
        for(int i :nums)
            System.out.print(i+" ");
        /* 之前:2 5 0 4 1 -10
         * 结果:1 1 1 1 1 1 
         */
```

Arrays.fill(Object[] array,int from,int to,Object object)
功能：对数组的部分元素填充一个值,从起始位置到结束位置，取头不取尾

```java
int[] nums = {2,5,0,4,1,-10};
        //对数组元素下标2到4的元素赋值为3
        Arrays.fill(nums,2,5,3);
        for(int i :nums)
            System.out.print(i+" ");
        /* 之前:2 5 0 4 1 -10
         * 结果:2 5 3 3 3 -10 
         */
```

3.Arrays.toString(Object[] array)
功能：返回数组的字符串形式

```java
int[] nums = {2,5,0,4,1,-10};
    System.out.println(Arrays.toString(nums));
    /*
     * 结果:[2, 5, 0, 4, 1, -10]
     */
```

4.Arrays.deepToString(Object[][] arrays)
功能：返回多维数组的字符串形式

```java
int[][] nums = {{1,2},{3,4}};
        System.out.println(Arrays.deepToString(nums));
        /*
         * 结果:[[1, 2], [3, 4]]
         */
```

5、Arrays.copyOfRange
对数组进行复制
与使用System.arraycopy进行数组复制类似的， Arrays提供了一个copyOfRange方法进行数组复制。

不同的是System.arraycopy，需要事先准备好目标数组，并分配长度。 copyOfRange 只需要源数组就就可以了，通过返回值，就能够得到目标数组了。
除此之外，需要注意的是 copyOfRange 的第3个参数，表示源数组的结束位置，是取不到的。

```java
import java.util.Arrays;
 
public class HelloWorld {
    public static void main(String[] args) {
        int a[] = new int[] { 18, 62, 68, 82, 65, 9 };
 
        // copyOfRange(int[] original, int from, int to)
        // 第一个参数表示源数组
        // 第二个参数表示开始位置(取得到)
        // 第三个参数表示结束位置(取不到)
        int[] b = Arrays.copyOfRange(a, 0, 3);
 
        for (int i = 0; i < b.length; i++) {
            System.out.print(b[i] + " ");
        }
 
    }
}
```

　　而用System.arraycopy进行复制的话如下

```java
public class HelloWorld {
    public static void main(String[] args) {
        int a [] = new int[]{18,62,68,82,65,9};
          
        int b[] = new int[3];//分配了长度是3的空间，但是没有赋值
          
        //通过数组赋值把，a数组的前3位赋值到b数组
          
        //方法一： for循环
          
        for (int i = 0; i < b.length; i++) {
            b[i] = a[i];
        }
         
        //方法二: System.arraycopy(src, srcPos, dest, destPos, length)
        //src: 源数组
        //srcPos: 从源数组复制数据的启始位置
        //dest: 目标数组
        //destPos: 复制到目标数组的启始位置
        //length: 复制的长度      
        System.arraycopy(a, 0, b, 0, 3);
          
        //把内容打印出来
        for (int i = 0; i < b.length; i++) {
            System.out.print(b[i] + " ");
        }
    }
}
```

6、Arrays.binarySearch()
查询元素出现的位置
使用binarySearch进行查找之前，必须使用sort进行排序

```java
import java.util.Arrays;
  
public class HelloWorld {
    public static void main(String[] args) {
        int a[] = new int[] { 18, 62, 68, 82, 65, 9 };
  
        Arrays.sort(a);
  
        System.out.println(Arrays.toString(a));
        //使用binarySearch之前，必须先使用sort进行排序
        System.out.println("数字 62出现的位置:"+Arrays.binarySearch(a, 62));
    }
}
```

