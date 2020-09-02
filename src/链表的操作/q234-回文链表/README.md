## 234.回文链表

##### 请判断一个链表是否为回文链表

```
输入: 1->2
输出: false

输入: 1->2->2->1
输出: true

进阶：
你能否用 O(n) 时间复杂度和 O(1) 空间复杂度解决此题？
```

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
class Solution {            
    public boolean isPalindrome(ListNode head) {
        float left = 0,right = 0,t = 1;    
        while(head != null) {
            left = left*10 + head.val; //记录正序的数字
            right = right + t*head.val;     //记录倒序的数字
            t = t*10;
            head = head.next;
        }
        return left == right;
    }
}
```

##### 思路：直接上进阶版吧，拿到题目的第一想法就是用栈，判断进栈和出栈的是否相等，但是不满足O（1）空间复杂度，因为这是个数字链表，所以可以用数学方法，定义三个变量满足空间复杂度，然后遍历数字，例如1，2，2，1，一个记录从后面接上，1，12，122，1221；一个记录从前面接上，1，21，221，1221；return  变量1==变量2；

