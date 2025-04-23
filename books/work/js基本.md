
# js 基本知识

## 基本语法

### 基本语法详情

##### 问题：const key in obj 和 const key of obj 的区别

**key in**用于对象，会遍历继承的属性，需要hasOwnProperty来守护,不保证遍历键的顺序 ,**key of**用于数组和可迭代对象不会遍历继承的属性,可以保证遍历键的顺序.
