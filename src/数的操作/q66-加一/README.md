## 66.加一

##### 给定一个由**整数**组成的**非空**数组所表示的非负整数，在该数的基础上加一。

##### 最高位数字存放在数组的首位， 数组中每个元素只存储**单个**数字。

##### 你可以假设除了整数 0 之外，这个整数不会以零开头。

```java
class Solution {
    public int[] plusOne(int[] digits) {
        for(int i = digits.length - 1; i >= 0; i --) {
            if(digits[i] != 9) {
                digits[i] ++;
                return digits;
            }           
            digits[i] = 0;
        }    
        int[] newDigits = new int[digits.length + 1];
        newDigits[0] = 1;
        return newDigits; 
    }
}
```

##### 思路：倒序遍历，不等于9的时候该数字+1然后return掉，等于9的时候该数字变成0然后不return，继续遍历，相当于进了一位；

##### 如果在for循环中没有return掉，说明该数字第一位是9，一直在进一位，则表示数组溢出，此时创建一个长度+1的新数组且给最高位赋值为1；