## 189.旋转数组

##### 给定一个数组，将数组中的元素向右移动 *k* 个位置，其中 *k* 是非负数。

```
输入: [1,2,3,4,5,6,7] 和 k = 3
输出: [5,6,7,1,2,3,4]
解释:
向右旋转 1 步: [7,1,2,3,4,5,6]
向右旋转 2 步: [6,7,1,2,3,4,5]
向右旋转 3 步: [5,6,7,1,2,3,4]
```

```java
		//这个是比较无脑的解法
class Solution {
    public void rotate(int[] nums, int k) {
       int[] tmp = new int[k];
        if(nums.length>=k){
            for (int i = nums.length - k, j = 0; i < nums.length; i++, j++) {
            tmp[j] = nums[i];
            }
            for (int i = nums.length - 1; i > k - 1; i--) {
                nums[i] = nums[i - k];			
            }
            for (int i = 0; i < k; i++) {
                nums[i] = tmp[i];
            }
        }else{
            k -= nums.length;
            for (int i = nums.length - k, j = 0; i < nums.length; i++, j++) {
            tmp[j] = nums[i];
            }
            for (int i = nums.length - 1; i > k - 1; i--) {
                nums[i] = nums[i - k];			
            }
            for (int i = 0; i < k; i++) {
                nums[i] = tmp[i];
            }
        }
    }
}

		//翻转，时间复杂度O(n)，空间复杂度O(1)
class Solution {
    public void rotate(int[] nums, int k) {
       int n = nums.length;
        k %= n;
        reverse(nums, 0, n - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, n - 1);
    }
    private void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start++] = nums[end];
            nums[end--] = temp;
        }
    }
}
```

##### 翻转思路：

```angelscript
nums[] = [1,2,3,4,5] 	右移两位--> [4,5,1,2,3] 
假设 n = nums.length，k = 右移位数，可得：  
     [1,2,3,4,5] --翻转索引为[0,n-1]之间的元素--> [5,4,3,2,1] 
                 --翻转索引为[0,k-1]之间的元素--> [4,5,3,2,1] 
                 --翻转索引为[k,n-1]之间的元素--> [4,5,1,2,3]
                 
旋转数组其实就是把数组分成了两部分，解题关键就是在保证原有顺序的情况下
把后面一部分移到前面去。数组整体翻转满足了第二个要素，但是打乱了数组的
原有顺序，所以此时再次对两部分进行翻转，让他们恢复到原有顺序（翻转之后
再翻转，就恢复成原有顺序了）。


执行流程：
第一次：54321，第二次：34521，第三次：34512
```
