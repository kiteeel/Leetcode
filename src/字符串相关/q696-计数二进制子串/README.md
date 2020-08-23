## 696.计数二进制子串

##### Q.给定一个字符串 s，计算具有相同数量0和1的非空(连续)子字符串的数量，并且这些子字符串中的所有0和所有1都是组合在一起的。

##### 重复出现的子串要计算它们出现的次数。

```java
class Solution {
    public int countBinarySubstrings(String s) {
        char arr[] = s.toCharArray();
		int pre = 0;
		int cur = 1;
		int res = 0;
		for (int i = 0; i < arr.length-1; i++) {
			if (arr[i] == arr[i + 1]) {
				cur++;
			} else {
				pre = cur;
				cur = 1;
			}
			if (pre >= cur) {
				res++;
			}
		}
        return res;
    }
}
```

![](F:\git\temp\src\images\696.计数二进制子串.png)