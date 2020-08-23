## 78.子集

##### 给定一组**不含重复元素**的整数数组 *nums*，返回该数组所有可能的子集（幂集）。

**说明：**解集不能包含重复的子集。

```
示例:
输入: nums = [1,2,3]
输出:
[
  [],
  [1],
  [2],
  [3],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2]  
]
```

```java
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> res = new ArrayList();
		res.add(new ArrayList());
		for (int i = 0; i < nums.length; i++) {
			int all = res.size();
			for (int j = 0; j < all; j++) {
				List<Integer> tmp = new ArrayList<>(res.get(j));
                tmp.add(nums[i]);
                res.add(tmp);
			}
		}
		return res;
    }
}
```

##### 思路：看示例可以得出，[1,2]和[2,1]属于重复子集，那么只需要将数组遍历一遍，然后加入list中再加后面一位元素再加入；

```
执行流程：
          son：  [1]  		,father：  [[], [1]]
          son：  [2]  		,father：  [[], [1], [2]]
          son：  [1, 2]  	,father：  [[], [1], [2], [1, 2]]
          son：  [3]  		,father：  [[], [1], [2], [1, 2], [3]]
          son：  [1, 3]  	,father：  [[], [1], [2], [1, 2], [3], [1, 3]]
          son：  [2, 3]  	,father：  [[], [1], [2], [1, 2], [3], [1, 3], [2, 3]]
          son：  [1, 2, 3] 	,father：  [[], [1], [2], [1, 2], [3], [1, 3], [2, 3], [1, 2, 3]]

          result：[[], [1], [2], [1, 2], [3], [1, 3], [2, 3], [1, 2, 3]]
```

