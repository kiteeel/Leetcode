## 581.最短无序连续子数组

##### 给定一个整数数组，你需要寻找一个**连续的子数组**，如果对这个子数组进行升序排序，那么整个数组都会变为升序排序。

##### 你找到的子数组应是**最短**的，请输出它的长度。

```
输入: [2, 6, 4, 8, 10, 9, 15]
输出: 5
解释: 你只需要对 [6, 4, 8, 10, 9] 进行升序排序，那么整个表都会变为升序排序。
```

**说明**:

1. 输入的数组长度范围在 [1, 10,000]。
2. 输入的数组可能包含**重复**元素 ，所以**升序**的意思是**<=。**

```java
class Solution {
    public int findUnsortedSubarray(int[] nums) {
        int max = nums[0];
        int min = nums[nums.length-1];
        int l = 0, r = -1;
        for(int i=0;i<nums.length;i++){
            if(max>nums[i]){
                r = i;
            }else{
                max = nums[i];
            }
            if(min<nums[nums.length-i-1]){
                l = nums.length-i-1;
            }else{
                min = nums[nums.length-i-1];
            }
        }
        return r-l+1;
    }
}
```

##### 思路：判定左右边界

- 右边界的定义：右边界的左边一定存在一个比右边界大的数，导致它不能在右边界这个位置，
- 左边界的定义：左边界的右边一定存在一个比左边界小的数，导致它不能在左边界这个位置。
