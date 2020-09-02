## 226.翻转二叉树

翻转一棵二叉树。

```
示例：
        输入：
             4
           /   \
          2     7
         / \   / \
        1   3 6   9
        
        输出：
             4
           /   \
          7     2
         / \   / \
        9   6 3   1
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
    public TreeNode invertTree(TreeNode root) {
        if(root == null)
            return root;
        TreeNode tmp = root.left;
        root.left = invertTree(root.right);
        root.right = invertTree(tmp);
        return root;
    }
}
```

##### 思路：前序遍历，然后递归，定义一个中间树存放left，然后左右翻转；
