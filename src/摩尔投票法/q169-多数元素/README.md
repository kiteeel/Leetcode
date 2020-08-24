## 169.多数元素

##### 给定一个大小为 *n* 的数组，找到其中的多数元素。多数元素是指在数组中出现次数**大于** `⌊ n/2 ⌋` 的元素。

##### 你可以假设数组是非空的，并且给定的数组总是存在多数元素。

```java
class Solution {
    public int majorityElement(int[] nums) {
        int res = nums[0];
        int count=1;
        for(int num:nums){
            if(num != res){
                count--;
                if(count == 0){
                    count=1;
                    res = num;
                }                
            }
            else{
                count++;
            }
        }
        return res;
    }
}
```

##### 思路：从第一个数开始count=1，遇到相同的就加1，遇到不同的就减1，减到0就重新换个数开始计数，最终能找到最多的那个，该方法叫做摩尔投票法；

##### 摩尔投票法基于这样一个事实，**当一个数的重复次数超过数组长度的一半，每次将两个不相同的数删除，最终剩下的就是要找的数。**