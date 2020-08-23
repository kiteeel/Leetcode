## 38.外观数列

##### 给定一个正整数 n（1 ≤ n ≤ 30），输出外观数列的第 n 项。

##### 注意：整数序列中的每一项将表示为一个字符串。

##### 「外观数列」是一个整数序列，从数字 1 开始，序列中的每一项都是对前一项的描述。前五项如下：

```
1.     1
2.     11
3.     21
4.     1211
5.     111221
```

##### 第一项是数字 1

##### 描述前一项，这个数是 1 即 “一个 1 ”，记作 11

##### 描述前一项，这个数是 11 即 “两个 1 ” ，记作 21

##### 描述前一项，这个数是 21 即 “一个 2 一个 1 ” ，记作 1211

##### 描述前一项，这个数是 1211 即 “一个 1 一个 2 两个 1 ” ，记作 111221

```java
class Solution {
    public String countAndSay(int n) {
        String s = "1";
        for(int i=2;i<=n;i++){
            s = toConver(s);
        }
        return s;
    }
    String toConver(String s){
        int len = s.length();
        int count=0;
        StringBuilder sb = new StringBuilder();
        char num = s.charAt(0);
        int i=0;
        while(i<len){
            if(num == s.charAt(i)){
                count++;
                i++;
            }else{
                sb.append(count).append(num);
                count=1;
                num=s.charAt(i);
                i++;
            }
        }
        sb.append(count).append(num);
        return sb.toString();
    }
}
```

