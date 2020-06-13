<!--
 * @Author: your name
 * @Date: 2020-06-12 19:54:45
 * @LastEditTime: 2020-06-12 22:01:46
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day12.md
-->

## 146. LRU缓存机制

<https://leetcode-cn.com/problems/lru-cache/>

## 我的回答

```js
function ListNode(key, val) {
    this.key = key
    this.val = val
    this.prev = null        //后指针
    this.next = null        //前指针
}

function LRUcache(capacity) {
    this.capacity = capacity        //保存该数据结构最大容量
    this.head = new ListNode()      //创建一个从头节点开始的链表
    this.tail = new ListNode()      //创建一个从尾节点开始的链表
    this.head.next = this.tail
    this.tail.prev = this.head
    this.size = 0
    this.data = new Map()
}

function get(key) {
    if(this.data.has(key)) {        //如果集合中存在key
        let node = this.data.get(key)      //获取key对应的值
        this.
        this.
        return node     //返回值
    }else {
        return -1
    }
}

function put(key, val) {
    let node
    if(this.data.has(key)) {        //如果集合中存在key
        node = this.data.get(key)   //获取key对应的值
        this.
        node = val      //更新值
    }else {
        node = new ListNode(key, val)
        this.data.get(key) = node
        if(this.size < this.capacity) {     //如果容量未满
            this.size++
        }else {
            key = 
            this.data.delete(key)
        }
    }
    this.
}

function removeNode(node) {
    let preNode = node.prev
    let nextNode = node.next
    preNode.next = nextNode
    nextNode.pre = preNode
}

function appendHead(node) {
     
}
```
