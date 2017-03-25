<template>
    <div class="mdContainer">
        <div class="navContainer">
            <div class="nameContainer">OVEN-mdEditor</div>
        </div>
        <div class="mdBodyContainer">
            <div class="editContainer">
                <textarea name="" class="mdEditor" v-model="input" v-on:input="updateFn"></textarea>
            </div>
            <div class="previewContainer markdown-body" v-html="compiledMarkdown">
            </div>
        </div>
    </div>
</template>

<script>
    var marked = require('marked');
    import hljs from '../../static/js/highlight.min.js'
    marked.setOptions({
        renderer: new marked.Renderer(),
        gfm: true,
        tables: true,
        breaks: false,
        pedantic: false,
        sanitize: true,
        smartLists: true,
        smartypants: false,
        highlight: function(code) {
            return hljs.highlightAuto(code).value
        }
    })
    export default {
        name: 'markdown',
        props: ['mdValues'],
        data() {
            return {
                input: this.mdValues
            }
        },
        methods: {
            updateFn: function() {
                this.$emit('childevent', this.input);
            }
        },
        computed: {
            compiledMarkdown: function() {
                return marked(this.input, {
                    sanitize: true
                })
            }
        }
    }
</script>

<style lang="scss">
    //引入reset文件
    @import "../../static/css/reset";
    // 引入github的markdown样式文件
    @import "../../static/css/github-markdown.css";
    // 引入atom的代码高亮样式文件
    @import "../../static/css/atom-one-dark.min.css";
    
    /**/
    
    .mdContainer {
        width: 100%;
        height: 100%;
        background: lightblue;
        .navContainer {
            width: 100%;
            height: 36px;
            background: #fff;
            box-sizing: border-box;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: flex-start;
            align-items: center;
            padding: 0 10px;
            .nameContainer {
                color: lightblue;
            }
        }
        .mdBodyContainer {
            width: 100%;
            height: calc(100% - 36px);
            background: pink;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-sizing: border-box;
        }
    }
    
    // 编辑区域
    .editContainer {
        height: 100%;
        width: 50%;
        box-sizing: border-box;
        border-right: 1px solid #ddd;
        background: #333;
        color: #fff;
        padding: 10px;
        .mdEditor {
            height: 100%;
            width: 100%;
            background: transparent;
            outline: none;
            color: #fff;
            resize: none;
        }
    }
    
    // 预览区
    .previewContainer {
        width: 50%;
        height: 100%;
        box-sizing: border-box;
        background: #fff;
        overflow: auto;
        padding: 10px;
    }
</style>