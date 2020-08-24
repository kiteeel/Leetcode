## 119.杨辉三角||

##### 给定一个非负索引 *k*，其中 *k* ≤ 33，返回杨辉三角的第 *k* 行。给定一个非负索引 *k*，其中 *k* ≤ 33，返回杨辉三角的第 *k* 行。

```
示例:
        输入: 3
        输出: [1,3,3,1]
```

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<List<Integer>> res = new ArrayList<>();
		for (int i=0;i<rowIndex+1;i++){
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
		return res.get(rowIndex);
    }
}
```

##### 思路：和q118.杨辉三角一样，然后返回最后一个ArrayList；



#### **进阶：**

你可以优化你的算法到 *O*(*k*) 空间复杂度吗？

```java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> res = new ArrayList<>(rowIndex + 1);
        long cur = 1;
        for (int i = 0; i <= rowIndex; i++) {
            res.add((int) cur);
            cur = cur * (rowIndex-i) / (i+1);
        }
        return res;
    }     
}
```

##### 思路：找第rowIndex+1行的index与val的规律，用cur指向val，建立数学公式cur = cur * (rowIndex - index) / (index+1);