<!--
 * @Author: your name
 * @Date: 2020-06-04 11:23:01
 * @LastEditTime: 2020-06-04 21:41:04
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day4-1.md
--> 


## 80.删除排序数组中的重复项 II

## 题目链接

<https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array-ii/description/>

## 我的回答

```js
var removeDuplicates = function(nums) {
    let a = 0
    for(let i =0; i<nums.length-1; i++) {
        if(nums[i] === nums[i+1] ) {
            a++
            if(a === 2) {
                nums.splice(i+1,1)
                a--
                i--
            }
        }else {
            a = 0
        }
    }
    return .length
};
```

## 思路
给一个变量a赋值为0,作用是统计数字出现的次数. 遍历数组, 如果数组第一个值和下一个值相等,a加一. 如果第三个值还是和前面的值相等, 那么a = 2. 如果a = 2时, 删除第三个值, a减一,i减一. 如果第一个值和第二个值不相等,那么a重置为0