```js
//抽离的公共代码
const common = {
    data(){
        return {
            a:1,
            b:2
        }
    },
    created(){
        console.log(`common created`);
    },
    methods:{
        sum(){
            return this.a + this.b;
        }
    }
}


/**
 * 使用comp1,将会得到
 * common created
 * comp1 created 1 2 3
 * 
 */

const comp1 = {
    mixins:[common] //之所以是数组，是因为可以进入多个配置代码
    created(){
        console.log("comp1 created",this.a,this.b,this.sum);
    }
}

```
___

```js
//公共远程获取数据的代码
//具体的组件中需要提供一个远程获取的方法 fetchData
export default function (defaultDataValue = null) {
    return {
    data() {
        return {
            isLoading: true,
            data:defaultDataValue,
        }
    },
    async created() {
        this.data = await this.fetchData();
        this.isLoading = false;
        }
    }
}
```