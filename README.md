# vue-mdeditor

> A Vue.js project

## 运行实例

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```
## 使用方法

> 父组件中

```html
<!--编辑器组件，嵌入到任意父组件中-->
<markdown v-bind:mdValues="msg" @childevent="childEventHandler"></markdown>
```
```javascript
// 引入markdown组件
import markdown from '../components/markdown'
export default {
    name: 'index',
    data() {
        return {
            msg: '## Vue-markdownEditor' 
            //初始化markdown编辑器的内容，通过props传入子组件
        }
    },
    components: {
        markdown // 声明mardown组件
    },
    methods: {
        // 监听事件，接收子组件传过来的数据
        childEventHandler:function(res){
            this.msg=res;
        }
    }
}
```