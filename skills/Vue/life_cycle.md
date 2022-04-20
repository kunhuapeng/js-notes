# vue.js的生命周期

共分8个阶段：

1. `beforeCreate`

> 在实例初始化之后，数据观测者`data observer`和`event/watcher`事件配置之前调用

2. `created`

> 在实例创建完成后立即调用，此时，实例已完成：观测者，属性和方法的运算，`watch/event`事件回调，挂载阶段还没开始，`$el`属性目前不可见。

3. `beforeMount`

> 在挂载开始之前调用，相关的`render`函数首次调用。

4. `mounted`

> `el`被新创建的`vm.$el`替换，并且在挂载到实例上之后再调用该钩。如果`root`实例挂载了一个文档内元素，当调用`mounted`时`vm.$el`也在文档内。

5. `beforeUpdate`

> 在数据更新时调用，发生在虚拟`dom`重新渲染和打补丁之前。

6. `updated`

> 由于数据更改导致的虚拟`dom`重新渲染和打补丁，在这之后会调用该钩子。

7. `beforeDestroyed`

> 在实例销毁之前调用，在这一步，实例仍然完全可用。

8. `destroyed`

在`vue.js`实例销毁后调用，`vue.js`实例指示的所有东西都会解除绑定，所有的事件监听会被移除，所有的子实例也会被销毁。

如果使用组件的`keep-alive`功能时，增加两个周期：

- `activated`在`keep-alive`组件激活时调用；
- `deactivated`在`keep-alive`组件停用时调用。

`<keep-alive>`包裹动态组件时，会缓存不活动的组件实例，而不是销毁它们。`<keep-alive>`是一个抽象组件，它自身不会渲染一个`DOM`元素，也不会出现在父组件链中。

当在`<keep-alive>`内切换组件时，它的`activated`和`deactivated`这两个生命周期钩子函数将会执行。

```vue
<keep-alive>
 <component :is="view"></component>
</keep-alive>
```

增加一个周期钩子：`ErrorCaptured`表示当捕获一个来自子孙组件的错误时调用。