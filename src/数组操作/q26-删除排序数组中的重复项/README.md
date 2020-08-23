## 26.删除排序数组中的重复项

##### 给定一个排序数组，你需要在**[ 原地](http://baike.baidu.com/item/原地算法)** 删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

##### 不要使用额外的数组空间，你必须在 **[原地 ](https://baike.baidu.com/item/原地算法)修改输入数组** 并在使用 O(1) 额外空间的条件下完成。

```java
public class LeetCodeTest {
	public static void main(String[] args) {
		int[] nums = {0,0,1,1,1,2,3,4};
		int j = 0;
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] != nums[j])
                nums[++j] = nums[i];
        }
        System.out.println(j+1);
	}
}
```

