## 191.位1的个数

##### 编写一个函数，输入是一个无符号整数，返回其二进制表达式中数字位数为 ‘1’ 的个数（也被称为[汉明重量](https://baike.baidu.com/item/汉明重量)）。

##### 提示：

请注意，在某些语言（如 Java）中，没有无符号整数类型。在这种情况下，输入和输出都将被指定为有符号整数类型，并且不应影响您的实现，因为无论整数是有符号的还是无符号的，其内部的二进制表示形式都是相同的。
在 Java 中，编译器使用二进制补码记法来表示有符号整数。因此，在上面的 示例 3 中，输入表示有符号整数 -3。

```java
//暴力法，直接计算1的个数
public class Solution {
    // you need to treat n as an unsigned value （您需要将n视为无符号值）
    public int hammingWeight(int n) {
        String s = Integer.toBinaryString(n);	//该方法把一个10进制数转为32位的2进制数。同时对负数，会用补码表示。
		int res = 0;
        for (int i = 0; i < s.length(); i++) {
			if (s.charAt(i)=='1') {
				res++;
			}
		}
        return res;
    }
}
//暴力法的简洁版，性能极差，写着玩hhhh
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        return Integer.toBinaryString(n).replaceAll("0", "").length();
    }
} 

//位运算
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        int count = 0;
        for (int i = 0; i < 32; i++) {
            if (((1 << i) & n) != 0) count++;
        }
        return count;
    }
}
//与运算的简洁版
public class Solution {
    // you need to treat n as an unsigned value
    public int hammingWeight(int n) {
        return n == 0 ? 0 : hammingWeight(n & (n - 1))+1;
    }
} 
```

##### 与运算的思路：如果是0结尾，向前借1，就会导致‘与’运算之后相较于运算之前相比少一个1，如果是1同样也导致运算之后相较于运算之前少一个1。循环往复。如果是0结尾，向前借1，就会导致‘与’运算之后相较于运算之前相比少一个1，如果是1同样也导致运算之后相较于运算之前少一个1。循环往复。
