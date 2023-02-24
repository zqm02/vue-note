# 事件总线

1.提供监听某个事件的接口  
2.提供取消监听的接口  
3.触发事件的接口(可传递数据)  
4.触发事件会自动通知监听者

```js
const listeners = {};

export default {
  //监听某一个事件
  $on(eventName, handler) {
    if (!listeners[eventName]) {
      listeners[eventName] = new Set();
    }
    listeners[eventName].add(handler);
  },
  //取消监听
  $off(eventName, handler) {
    if (!listeners[eventName]) {
      return;
    }
    listeners[eventName].delete(handler);
  },
  //触发事件
  $emit(eventName, ...args) {
    if (!listeners[eventName]) {
      return;
    }
    for (const handler of listeners[eventName]) {
      handler(...args);
    }
  },
};
```

```js
import Vue from "vue";
export default app = new Vue({});
```
