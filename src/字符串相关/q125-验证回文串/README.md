## 125.验证回文串

##### 给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

**说明：**本题中，我们将空字符串定义为有效的回文串。

```java
class Solution {
    public boolean isPalindrome(String s) {
        if(s.isEmpty())			
			return true;
        s = s.toLowerCase();
		StringBuilder sb = new StringBuilder(s.length());
		for (char c : s.toCharArray()) {
            if ((c >= '0' && c <= '9') || (c >= 'a' && c <= 'z')) {
                sb.append(c);
            }
        }
		return sb.toString().equals(sb.reverse().toString());
    }
}		//暴力解法：大写转小写，遍历掉不要的字符，字符串反转，return与反转前的对比
```

