## 283.移动零

##### 给定一个数组 `nums`，编写一个函数将所有 `0` 移动到数组的末尾，同时保持非零元素的相对顺序。

```
示例:
        输入: [0,1,0,3,12]
        输出: [1,3,12,0,0]
```

**说明**:

1. 必须在原数组上操作，不能拷贝额外的数组。
2. 尽量减少操作次数。

```java
class Solution {
    public void moveZeroes(int[] nums) {
        for (int i = 0, count = 0; i < nums.length; i++) {
			if (nums[i] != 0) {
				if (count != i) {
					nums[count] = nums[i];
					nums[i] = 0;
				}
				count++;
			}
		}
    }
}
```

##### 思路：非常简单的做法就是双指针，一个用来遍历，一个用来指向0的元素，然后做替换操作，并更新指针位置；
