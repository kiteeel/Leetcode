## 118.杨辉三角

##### 给定一个非负整数 *numRows，*生成杨辉三角的前 *numRows* 行

```
示例:
        输入: 5
        输出:
        [
             [1],
            [1,1],
           [1,2,1],
          [1,3,3,1],
         [1,4,6,4,1]
        ]
```

```java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<>();
		for (int i=0;i<numRows;i++){
            ArrayList<Integer> tmp=new ArrayList<Integer>();
            for (int j=0;j<=i;j++){
            	//第一个位置和最后一个位置的元素为1
                if (j==0 || j==i){
                	tmp.add(1);
                }else {
                    //上一行的元素进行相加
                	tmp.add(res.get(i-1).get(j-1)+res.get(i-1).get(j));
                }
            }
            res.add(tmp);
        }
		return res;
    }
}
```

##### 思路：两个遍历嵌套，一个遍历行，一个遍历列，除去头和尾，根据上一列的元素生成当前列；