<!--
 * @Author: your name
 * @Date: 2020-06-02 19:19:46
 * @LastEditTime: 2020-06-03 21:47:37
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day2.md
--> 

# 75.颜色分类

## 题目链接

<https://leetcode-cn.com/problems/sort-colors/>

## 我的回答

```js
var sortColors = function(nums) {
    let l = 0, r = nums.length -1, i = 0
    while(i<=r) {
      if(nums[i] === 0) {
        [nums[i],nums[l]] = [nums[l],nums[i]]
        l++
        i++
        continue
      }
      if(nums[i] === 1) {
        i++
        continue
      }
      if(nums[i] === 2) {
        [nums[i],nums[r]] = [nums[r],nums[i]]
        r--
        continue
      }
    }
    return nums
};
```

时间复杂度O(n)
空间复杂度O(1)

思路:
当数组左边第一个为2时,与数组最后一位互换,右指针减一
当数组左边第一个为0时,与左指针的值互换,第三指针加一, 左指针加一
当数组左边第一个为1时,第三指针加一
0对应左指针往左边排,2对应右指针往右边排,遇到1跳过,第三指针对应数组下标遍历,当所有0和2排完后,1只会在中间的位置