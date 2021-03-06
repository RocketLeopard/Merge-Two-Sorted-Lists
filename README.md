# Merge-Two-Sorted-Lists（合并两个有序链表）
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

## Sample
输入：1->2->4, 1->3->4  
输出：1->1->2->3->4->4  

## Solution
方法一：递归  
核心就是两个链表头部较小的一个与剩下元素的merge操作结果合并

方法二：迭代  
首先，我们设定一个头指针head，这可以方便在最后返回合并后的链表。维护一个prev指针，需要做的是调整它的next指针。
然后，重复以下过程，直到l1或者l2指向了 null：  
如果l1当前位置的值小于等于l2，就把l1的值接在prev节点的后面同时将l1指针往后移一个。否则，对l2做同样的操作。不管将哪一个元素接在了后面，都把prev向后移一个元素。  
在循环终止的时候，l1和l2至多有一个是非空的。由于输入的两个链表都是有序的，所以不管哪个链表是非空的，它包含的所有元素都比前面已经合并链表中的所有元素都要大。这意味着只需要简单地将非空链表接在合并链表的后面，并返回合并链表。

## 复杂度分析
方法一：递归  
时间复杂度：O(N+M)。 因为每次调用递归都会去掉l1或者l2的头元素（直到至少有一个链表为空），函数mergeTwoList中只会遍历每个元素一次。所以，时间复杂度与合并后的链表长度为线性关系。  
空间复杂度：O(N+M)。调用mergeTwoLists退出时，l1和l2中每个元素都一定已经被遍历过了，所以N+M个栈帧会消耗O(N+M)的空间。  

方法二：迭代    
时间复杂度：O(N+M) 。因为每次循环迭代中，l1和l2只有一个元素会被放进合并链表中，while循环的次数等于两个链表的总长度。所有其他工作都是常数级别的，所以总的时间复杂度是线性的。  
空间复杂度：O(1)。迭代的过程只会产生几个指针，所以它所需要的空间是常数级别的。  

## 备注
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/merge-two-sorted-lists
