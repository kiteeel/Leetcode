## 101.对称二叉树

给定一个二叉树，检查它是否是镜像对称的。（左右对称）

```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public boolean isSymmetric(TreeNode root) {
        if(root == null)
            return true;
        return check(root.left,root.right);
    }
    public boolean check(TreeNode t1, TreeNode t2){
        if(t1 == null && t2 == null) return true;
        if(t1 == null || t2 == null) return false;
        if(t1.val != t2.val) return false;
        return check(t1.left, t2.right) && check(t1.right, t2.left);
    }
}
```

##### 思路：首先传入的是根节点root，如果根节点为null则为对称，如果不为null，则接下来判断根节点的左子节点和右子节点的val是否相等，如果成立再判断左子节点的左子节点和右子节点的右子节点是否相当，而这个判断左右相等的循环操作则可以作为递归条件开始递归；