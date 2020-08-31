## 461.汉明距离

##### 两个整数之间的[汉明距离](https://baike.baidu.com/item/汉明距离)指的是这两个数字对应二进制位不同的位置的数目。

##### 给出两个整数 `x` 和 `y`，计算它们之间的汉明距离。

**注意：**
0 ≤ `x`, `y` < 231.

```
示例:
    输入: x = 1, y = 4

    输出: 2

    解释:
    1   (0 0 0 1)
    4   (0 1 0 0)
           ↑   ↑

    上面的箭头指出了对应二进制位不同的位置。
```

```java
class Solution {
    public int hammingDistance(int x, int y) {
        int z = x ^ y;
        int count = 0;
        while(z != 0){
            z = z & (z-1);
            count++;
        }
        return count;
    }
}
```

##### 异或运算符是用符号“^”表示的，其运算规律是：

##### 两个操作数的位中，相同则结果为0，不同则结果为1。
