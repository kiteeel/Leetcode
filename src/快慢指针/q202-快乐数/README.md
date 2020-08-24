## 202.快乐数

##### 编写一个算法来判断一个数 `n` 是不是快乐数。

##### 「快乐数」定义为：对于一个正整数，每一次将该数替换为它每个位置上的数字的平方和，然后重复这个过程直到这个数变为 1，也可能是 无限循环 但始终变不到 1。如果 可以变为  1，那么这个数就是快乐数。

##### 如果 `n` 是快乐数就返回 `True` ；不是，则返回 `False` 。

```
示例:
        输入：19
        输出：true
        解释：
        12 + 92 = 82
        82 + 22 = 68
        62 + 82 = 100
        12 + 02 + 02 = 1
```

##### 分析一下，这道题主要是找到跳出死循环的条件，循环就一定会有循环周期，可以用快慢指针来判断循环周期，如果不是循环1就false，否则true；

```java
class Solution {
    public boolean isHappy(int n) {
        int fast=n;
        int slow=n;
        do{
            slow=squareSum(slow);
            fast=squareSum(fast);
            fast=squareSum(fast);
        }while(slow!=fast);
        if(fast==1)
            return true;
        return false;
    }   
    private int squareSum(int m){
        int squaresum=0;
        while(m!=0){
           squaresum+=(m%10)*(m%10);
            m/=10;
        }
        return squaresum;
    }  
}
```

