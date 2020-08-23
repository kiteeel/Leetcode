## 3.无重复字符的最长子串

##### 给定一个字符串，请你找出其中不含有重复字符的 **最长子串** 的长度

```
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int[] last = new int[128];
        int res = 0;
        int start = 0; // 窗口开始位置
        for(int i = 0; i < s.length(); i++) {
            int index = s.charAt(i);				//原本返回char类型，直接返回int记录上次出现的位置省略了字符的比较
            start = Math.max(start, last[index]);
            res   = Math.max(res, i - start + 1);
            last[index] = i + 1;
        }
        return res;
    }
}
```

