<!--
 * @Author: your name
 * @Date: 2020-06-06 20:35:17
 * @LastEditTime: 2020-06-06 20:45:30
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \91days-algorithm\day6.md
--> 

## 380. 常数时间插入、删除和获取随机元素

<https://leetcode-cn.com/problems/insert-delete-getrandom-o1/>

## 我的回答

```js
/**
 * Initialize your data structure here.
 */
var RandomizedSet = function() {
    this.set = new Set()
};

/**
 * Inserts a value to the set. Returns true if the set did not already contain the specified element. 
 * @param {number} val
 * @return {boolean}
 */
RandomizedSet.prototype.insert = function(val) {
    if(this.set.has(val)) {
        return false
    }else {
        this.set.add(val)
        return true
    }
};

/**
 * Removes a value from the set. Returns true if the set contained the specified element. 
 * @param {number} val
 * @return {boolean}
 */
RandomizedSet.prototype.remove = function(val) {
    if(this.set.has(val)) {
        this.set.delete(val)
        return true
    }else{
        return false
    }
};

/**
 * Get a random element from the set.
 * @return {number}
 */
RandomizedSet.prototype.getRandom = function() {
    let arr = Array.from(this.set)
    if(this.set.size === 1) {
        return arr[0]
    }
    let random = Math.floor(Math.random() * this.set.size)
    return arr[random]
};

/**
 * Your RandomizedSet object will be instantiated and called as such:
 * var obj = new RandomizedSet()
 * var param_1 = obj.insert(val)
 * var param_2 = obj.remove(val)
 * var param_3 = obj.getRandom()
 */
```

使用ES6中的Set集合方法