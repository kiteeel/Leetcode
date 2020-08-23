## 88.合并两个有序数组

##### 给你两个有序整数数组 *nums1* 和 *nums2*，请你将 *nums2* 合并到 *nums1* 中*，*使 *nums1* 成为一个有序数组。

##### 说明:

初始化 nums1 和 nums2 的元素数量分别为 m 和 n 。
你可以假设 **nums1 有足够的空间**（空间大小大于或等于 m + n）来保存 nums2 中的元素。

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int p = m-- + n-- - 1;
        while (m >= 0 && n >= 0) {
            nums1[p--] = nums1[m] > nums2[n] ? nums1[m--] : nums2[n--];
        }
        
        while (n >= 0) {
            nums1[p--] = nums2[n--];
    }
}
```

##### 思路：假设nums1有足够的空间，即后面都为0占位，三目运算符逆向判断当前指向的数值大小，如果nums2>nums1则直接给后面，否则赋值nums1中的当前指向的数传递给后面，这样就省略了后面再排序的步骤；这个nums1和nums2是一个动态的比较；

