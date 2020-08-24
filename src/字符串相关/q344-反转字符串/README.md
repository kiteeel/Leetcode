## 344.反转字符串

##### 编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 `char[]` 的形式给出。

##### 不要给另外的数组分配额外的空间，你必须**[原地](https://baike.baidu.com/item/原地算法)修改输入数组**、使用 O(1) 的额外空间解决这一问题。

##### 你可以假设数组中的所有字符都是 [ASCII](https://baike.baidu.com/item/ASCII) 码表中的可打印字符。

```java
class Solution {
    public void reverseString(char[] s) {
        char[] a = new char[s.length];	//这里不能直接用 char[] a = s; 否则会直接指向s的内存
		for (int i = 0; i < a.length; i++) {		
			a[i] = s[i];				//辅助s
		}
		for (int i = 0; i < a.length; i++) {
			s[i] = a[a.length-1-i];		//在原数组上修改反转后的内容
		}
    }
}
```

##### 思路：这里我是直接辅助数组然后反转字符串，看题目说可以假设数组中的所有字符都是 [ASCII](https://baike.baidu.com/item/ASCII) 码表中的可打印字符。说明可以根据ASCII的方式来操作，但是复杂度应该是差不多的，下次有兴趣再尝试