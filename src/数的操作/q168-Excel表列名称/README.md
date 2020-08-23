## 168.Excel表列名称

##### 给定一个正整数，返回它在 Excel 表中相对应的列名称。

```
例如：
	1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...

```

```java
class Solution {
    public String convertToTitle(int n) {
		if (n<=0) 
			return "";
		StringBuilder sb = new StringBuilder();
		while(n>0) {
			n--;		// 'A'~'Z'对应0~25
			sb.append((char)(n%26+'A'));	// ascii码加相应位数
			n/=26;		// 进位
		}
		return sb.reverse().toString();
    }
}
```

##### 思路：10进制转26进制；