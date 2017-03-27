# vue-mdeditor

> A Vue.js project

## 运行实例

``` bash
# install dependencies
cnpm install

# serve with hot reload at localhost:8080
cnpm run dev

# build for production with minification
cnpm run build

# build for production and view the bundle analyzer report
cnpm run build --report
```
## 使用方法
> 使用前必知

本markdown组件采用vue-cli模式开发，适用于此类开发模式，其他模式请自行修改。

> 安装依赖
```bash
# 本组件css采用sass编写，亦可修改为css(请自行修改)，核心依赖marked组件，请务必安装，谢谢
cnpm i node-sass sass-loader marked -D
```
> 配置要求
```html
<!--本组件使用font-awesome字体图标库，请于index.html提前引入-->
<link href="//cdn.bootcss.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">
```
```javascript
// 根据项目修改引入文件的路径（所需文件放在了static目录下）
var marked = require('marked');
import hljs from '../../static/js/highlight.min.js'
import range from '../../static/js/rangeFn.js'
```
```css
/*根据项目修改引入文件的路径（所需文件放在了static目录下）*/
/*引入reset文件*/
@import "../../static/css/reset";
/*引入github的markdown样式文件*/
@import "../../static/css/github-markdown.css";
/*引入atom的代码高亮样式文件*/
@import "../../static/css/atom-one-dark.min.css";
    
```

> 父组件中

```html
<!--编辑器组件，嵌入到任意父组件中-->
<markdown 
:mdValuesP="msg" 
:fullPageStatusP="false" 
:editStatusP="false" 
:previewStatusP="false"  
@childevent="childEventHandler">
</markdown>
<!--变量后面的大写P表示是从父组件中传入的参数-->
<!--:mdValuesP="msg" 表示需要初始化传入编辑器的内容-->
<!--:fullPageStatusP="false" 加载时是否全屏（true全屏/false跟随父容器）-->
<!--:editStatusP="false" 加载时是否显示编辑容器（true显示/false不显示）-->
<!--:previewStatusP="false" 加载时是否显示预览榕溪（true全屏/false不显示）-->
<!--@childevent="childEventHandler" 监听组件的$.emit()方法传回父组件的值，便于父容器保存获取-->

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
## 效果展示

![vue-mdeditor](http://static-oven.b0.upaiyun.com/github-resource/markdownEditor.png)

## 后期更新

1. 更多的语法支持
2. 更丰富的API文档
3. 更人性化的使用方式
4. 更傻瓜式的使用方式

> 喜欢就关注一下吧。@_@!!!