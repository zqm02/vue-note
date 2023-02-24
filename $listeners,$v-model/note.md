# $listeners

`$listeners`是`vue`的一个实例属性，它用于获取父组件传过来的所有时间函数

```html
<!--父组件-->
<Child @event1="handleEvent1" @event2="handleEvent2" />
```

```js
//子组件
this.$listeners; // {event1:handleEvent1,event2:handleEvent2}
```

> `$emit` 和 `$listeners` 通信的异同
> 相同点:均可实现子组件向父组件传递消息
>
> 差异点:
>
> - `$emit` 更加符合单向数据流，子组件仅发出通知，由父组件监听做出改变；而 `$listeners` 则是在子组件中直接使用了父组件的方法。
> - 调试工具可以监听到子组件 `$emit` 的事件，但无法监听到 `$listeners` 中的方法调用。
> - 由于 `$listeners` 中可以获得传递过来的方法，因此调用方法可以得到其返回值。但 `$emit` 仅仅是向父组件发出通知，无法知晓父组件处理的结果。

# v-model

`v-model`指令实质是一个语法糖，它是`value`属性和`input`事件的*结合体*

```html
<input :value="data" @input="data=$event.target.value" />
<!-- 等同于 -->
<input v-model="data" />
```

详见：[表单输入绑定](https://cn.vuejs.org/v2/guide/forms.html)
