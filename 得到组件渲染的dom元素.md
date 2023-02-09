## 得到组件生成的dom元素
```js
/** 
 * 获取某个组件渲染的Dom根元素
*/
    function getComponentRootDom(comp,props) {
        const vm = new Vue({
            render:(h)=>h(comp,{props}),
        });
        vm.$mount();
        return vm.$el;
    }
```


模板-->render函数


 $el:是一个实例成员，渲染出来的DOM根元素


## 扩展vue实例


### 向实例注入成员
```js
Vue.prototype.sayHello = function(){
    console.log("Hello");
}
```


细节：最好在sayHello前面加一个$,便于区分。


## ref
父组件拿子组件的属性

一般不直接操作dom，不符合vue的理念




## css module

需要将文件命名为`xxx.module.ooo`
`xxx`为文件名
`ooo`为样式文件后缀，可以是`css`,`less`