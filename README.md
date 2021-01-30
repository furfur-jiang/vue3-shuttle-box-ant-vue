# vue-shuttle-box

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

穿梭框的实现思路：
首先在temlate写左右两列，两个按钮
通过改变左右两列的数据，vue自动响应式地改变对应内容，然后通过按钮触发即可。
通过shuttle 函数实现过滤选中和未选择，分别赋予左右列，并合并原来的内容。
注意，由于改变了原来的数据，所以要先处理好先后顺序，否则会由于原数据被改而后续操作出现问题。

### Customize configuration
文章 [vue3+ts+ant-vue:手把手教你实现穿梭框简易版，配源码](https://blog.csdn.net/weixin_44523860/article/details/113441091).
