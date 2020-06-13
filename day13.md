<!--
 * @Author: your name
 * @Date: 2020-06-13 19:48:08
 * @LastEditTime: 2020-06-13 20:41:39
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day13.md
--> 

## 104.二叉树的最大深度

<https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/submissions/>

## 我的回答

```js
var maxDepth = function(root) {
    if(!root) {
        return 0
    }
    // else {
    //     return Math.max(maxDepth(root.left), maxDepth(root.right)) + 1
    // }
    let res = []
    let num = 0
    if(root != null) {
        res.push(root)
    }
    while(true) {
        let nodeCount = res.length
        if(nodeCount === 0) {
            return num
        }
        num++
        while(nodeCount > 0) {
                let node = res.shift()
                if(node.left != null) {
                    res.push(node.left)
                }
                if(node.right != null) {
                    res.push(node.right)
                }
                nodeCount--
        }
    }
};
```

思路: 创建一个数组存储节点,创建一个变量来储存层数
如果root为null,则返回,如果root为真,则push进数组
创建一个变量保存数组的长度,如果为0,则返回层数num
如果长度大于0, 移除数组第一位,同时长度减一. 如果该节点的左右节点为真,则push进数组,遍历完该层节点.回到上面更新长度和层数. 不断循环, 直到左右节点全部为null,则长度为0,退出循环

时间复杂度O(n),空间复杂度O(logN)