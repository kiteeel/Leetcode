## 171.Excel表列序号

##### 给定一个Excel表格中的列名称，返回其相应的列序号。

```
例如：
	A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...

```

```java
class Solution {
    public int titleToNumber(String s) {
        char[] charArray = s.toCharArray();
        int res = 0;
        for(int i = 0; i < charArray.length; i++) {
            res = res*26 + (charArray[i] - 'A' + 1);
        }     
        return res;
    }
}
```

##### 思路：26进制转换10进制；