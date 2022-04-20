# vue.js页面的闪烁

在`vue.js`有一个`v-cloak`指令，该指令一直保持在元素上，直到关联实例结束编译。当和`css`使用时，这个指令可以隐藏未编译的标签，直到实例编译结束：`<div>`不会显示，直到编译结束。

```vue
[v-cloak] {
 display: none;
}
<div v-cloak>{{dada}}</div>
```

