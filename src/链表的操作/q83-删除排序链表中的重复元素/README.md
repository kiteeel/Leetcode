## 83.删除排序链表中的重复元素

##### 给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。

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
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null) 
            return null;
        if (head.next == null) 
            return head;
        if (head.val == head.next.val) {
            head = deleteDuplicates(head.next);
        } else {
            head.next = deleteDuplicates(head.next);
        }
        return head;
    }
}
```

