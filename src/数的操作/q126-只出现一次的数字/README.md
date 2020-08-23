## 126.只出现一次的数字

##### 给定一个**非空**整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

**说明：**你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

```java
class Solution {
    public int singleNumber(int[] nums) {
        int res = 0;
        for(int i = 0;i<nums.length;i++)
            res ^=nums[i];
        return res;
    }
}
//	例如：int[] nums = {2,1,2,3,4,4,3}	=>	res = 2^1^2^3^4^4^3 => 交换律加结合率 => res = 1
```

```
思路：
        1.交换律：a ^ b ^ c <=> a ^ c ^ b

        2.任何数于0异或为任何数 0 ^ n => n

        3.相同的数异或为0: n ^ n => 0
```

