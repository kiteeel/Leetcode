## 69.x的平方根

##### 实现 `int sqrt(int x)` 函数。

##### 计算并返回 *x* 的平方根，其中 *x* 是非负整数。

##### 由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。

```java
class Solution {
    public int mySqrt(int x) {
        long a = 1;
        while(a*a<=x){
            a++;
        }
        int b = new Long(a).intValue();
        return b-1;
    }
}
```

##### 思路：假设x的平方根是n，遍历1到n的所有数，如果n*n大于x，则n-1满足题目条件；

##### 该方法比较暴力，所以耗时很久，为了性能应该采用二分法，可以更快的找到平方根，但是实现的代码量太大，没有采用这种方法；