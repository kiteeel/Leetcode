## 5.最长回文子串

##### 给定一个字符串 `s`，找到 `s` 中最长的回文子串。你可以假设 `s` 的最大长度为 1000

```java
class Solution {
    public String longestPalindrome(String s) {
        if (s.length() < 2) 
            return s;       
        int maxLen = 1;
        int begin = 0;
        char[] charArray = s.toCharArray();
        for (int i = 0; i < s.length() - 1; i++) {
            for (int j = i + 1; j < s.length(); j++) {
                if (j - i + 1 > maxLen && validPalindromic(charArray, i, j)) {
                    maxLen = j - i + 1;
                    begin = i;
                }
            }
        }
        return s.substring(begin, begin + maxLen);
    }
    private boolean validPalindromic(char[] charArray, int left, int right) {	//判断是否回文
        while (left < right) {
            if (charArray[left] != charArray[right]) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}
```

##### 思路：暴力求解，列出所有排列组合依次判断是否为回文，优化点：记录当前遍历到的最长回文子串长度，接下来遍历到小于或等于该长度的子串不进行遍历，节省时间。

```
执行用时：132 ms, 在所有 Java 提交中击败了30.42%的用户

内存消耗：37.9 MB, 在所有 Java 提交中击败了91.70%的用户
```

##### 使用动态规划的思想，可以增加内存的消耗来减少执行时间

