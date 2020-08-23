## 32.最长有效括号

##### 给定一个只包含 `'('` 和 `')'` 的字符串，找出最长的包含有效括号的子串的长度。

```java
class Solution {
    public int longestValidParentheses(String s) {
        Stack<Integer> stack=new Stack<Integer>();
    	// 向栈中预置一个-1，用于计算长度将计算长度的方式转化成“）”的下标减去出栈后栈顶元素的下标
    	stack.push(-1);
    	int len = 0;
    	for (int i = 0; i < s.length(); i++) {
			if ('('==s.charAt(i)) {
				stack.push(i);
			}
			if (')'==s.charAt(i)) {
				stack.pop();
				// 如栈空，则注入新的i作为预置下标(用于计算新的一串有效括号)
				if (stack.isEmpty()) {
					stack.push(i);
				}
				len = Math.max(len, i-stack.peek());//更新有效长度
			}
		}
    	return len;
    }
}
```
