## 112.路径总和

##### 给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。

**说明:** 叶子节点是指没有子节点的节点

```
示例: 
给定如下二叉树，以及目标和 sum = 22，
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1

return true;
```

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
    public boolean hasPathSum(TreeNode root, int sum) {
        if(root==null)
            return false;
        sum-=root.val;
        if(root.left==null&&root.right==null)
            return sum==0;
        return hasPathSum(root.left,sum)||hasPathSum(root.right,sum);
    }
}
```

##### 思路：首先根节点为空则返回false，然后找到递归条件，根节点不为空时将sum-root.val，然后将下一个左右子节点代入递归；

