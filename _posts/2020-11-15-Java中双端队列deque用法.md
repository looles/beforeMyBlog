## 介绍
Deque是一个线性collection，支持在两端插入和移除操作，名称deque是“double ended queue（双端队列）”的缩写，通常读为“deck”。大多数Deque实现对于它们能够包含的元素数没有固定限制，但此接口既支持有容量限制的双端队列，也支持没有固定大小限制的双端队列。
此接口定义在双端队列两端访问元素的方法。提供插入，移除和检查元素的方法。每种方法都存在两种形式：一种形式在操作失败时抛出异常，另一种形式返回一个特殊值（null或者false，具体取决于操作）。插入操作的后一种形式是专为使用有容量限制的Deque实现设计的，在大多数实现中，插入操作不能失败。

## 主要实现
 - ArrayDeque：基于数组实现的线性双向队列
 - LinkedList：基于链表实现的链式双向队列
 
## 特性

 1. 插入、删除、获取操作支持两种形式：抛出异常或者返回null或false
 2. 既具有FIFO特点又具有LIFO特点，既是队列又是栈
 3. 不推荐插入null元素，null作为特定返回值表示队列为空
 4. 未定义基于元素相等的equals和hashCode
 
## 常用方法
 1. 插入元素
 
			addFirst(): 向队头插入元素，如果元素为空，则发生NPE
			addLast(): 向队尾插入元素，如果为空，则发生NPE
			offerFirst(): 向队头插入元素，如果插入成功返回true，否则返回false
			offerLast(): 向队尾插入元素，如果插入成功返回true，否则返回false
			
 2. 移除元素
 
			removeFirst(): 返回并移除队头元素，如果该元素为null，则发生NoSuchElementException
			removeLast()：返回并移除队尾元素，如果该元素是null，则发生NoSuchElementException
			pollFirst(): 返回并移除队头元素，如果队列无元素，则返回null
			pollLast(): 返回并移除队尾元素，如果队列无元素，则返回null
			
 3. 获取元素
 
			getFirst(): 获取队头元素但不移除，如果队列无元素，则发生NoSuchElementException
			getLast(): 获取队尾元素但不移除，如果队列无元素，则发生NoSuchElementException
			peekFirst(): 获取队头元素但不移除，如果队列无元素，则返回null
			peekLast(): 获取对微元素但不移除，如果队列无元素，则返回null





