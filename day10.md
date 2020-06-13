<!--
 * @Author: your name
 * @Date: 2020-06-10 15:39:54
 * @LastEditTime: 2020-06-10 22:40:54
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day10.md
--> 


## 160. 相交链表

<https://leetcode-cn.com/problems/intersection-of-two-linked-lists/>

## 我的回答

1.has法
有A,B两条链表,先遍历其中一个, 比如将A中的所有节点存入Set
遍历B, 检查B中的节点是否在存放A的Set集合中. 如果存放,返回第一个节点

时间复杂度0(n), 空间复杂度O(n)

```JS
function hasfun(headA, headB) {
let data = new Set()    //存放A所有节点的地址

while (headA !== null) {    //A不为空
    data.add(headA)    //添加A的当前节点
    headA = headA.next    //移动到下一个节点
}
while (headB !== null) {    //B不为空
    if(data.has(headB)) {       //检测B的当前节点是否在Set集合中存在
        return headB
    }
    headB = headB.next          //如果不存在则指向B的下一个节点
}

return null         //如果遍历完没有则返回null,表示不存在
}
```

2.双指针
使用a, b两个指针分别指向headA, headB, 两个指针以相同的速度向后移动
当headA遍历完时,重新定位到headB,继续遍历B到相交点
当headB遍历完时,重新定位到headA,继续遍历A到相交点

时间复杂度0(n), 空间复杂度0(1)

```js
function twoPointer(headA, headB) {
    let a = headA
    let b = headB

    while(a != b) {
        a = a?a.next:headB
        b = b?b.next:headA
    }
    return a
 }
```




## 94. 二叉树的中序遍历

<https://leetcode-cn.com/problems/binary-tree-inorder-traversal/>


## 我的回答

```js
var inorderTraversal = function(root) {
    let result = []

    //递归
    // function treeAry(root) {
    //     if(root){
    //     if(root.left != null) {   //如果root.left为真,把root.left作为参数传入递归函数,在该函数中root等于之前的root.left
    //         treeAry(root.left)
    //     }
    //     result.push(root.val)
    //     if(root.right != null) {
    //         treeAry(root.right)
    //      }
    //     }
    // }
    //treeAry(root)

    //迭代
    if(!root) {
        return result
    }
    let stack = []

    while(root !== null || stack.length > 0) {
        if(root) {
            stack.push(root)        //把节点推入栈
            root = root.left        //root等于上一节点的左节点
        }else {
            let node = stack.pop()    //如果root为null, 保存出栈元素
            result.push(node.val)       //把出栈的节点推入result
            root = node.right           //root等于出栈节点的右节点
            }
        }
        return result
    }
```