## 206.反转链表

##### 反转一个单链表。

```
输入: 1->2->3->4->5->NULL
输出: 5->4->3->2->1->NULL

进阶:
你可以迭代或递归地反转链表。你能否用两种方法解决这道题？
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
    public ListNode reverseList(ListNode head) {
        ListNode pre = null;    //前节点指针
        ListNode cur = head;    //当前节点指针
        while(cur != null){
            ListNode nextTmp = cur.next;       //暂时存放当前节点的下一个节点，
            cur.next = pre;  //当前节点指向前一个节点
            pre = cur;  //前指针后移
            cur = nextTmp;  //当前指针后移
        }       
        return pre;
    }
}
```



