<template>
    <div class="indexContainer">
        <div class="editorContainer">
            <markdown 
            :mdValuesP="msg.mdValue"  
            :fullPageStatusP="false" 
            :editStatusP="false" 
            :previewStatusP="false" 
            :navStatusP="false"
            :icoStatusP="true"  
            @childevent="childEventHandler"
            ></markdown>
        </div>
    </div>
</template>

<script>
    import markdown from '../components/markdown'
    export default {
        name: 'index',
        data() {
            return {
                msg: {
                    mdValue:'## Vue-markdownEditor'
                }
            }
        },
        components: {
            markdown
        },
        methods: {
            childEventHandler:function(res){
                // res会传回一个data,包含属性mdValue和htmlValue，具体含义请自行翻译
                this.msg=res;
            }
        }
    }
</script>

<style lang="scss" scoped>
    .show{
        position: absolute;
        left: 0;
        top: 0;
    }
    .indexContainer {
        width: 100%;
        height: 100%;
        background: #ddd;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
    }
    
    .editorContainer {
        width: 90%;
        height: 90%;
        border: 1px solid #ddd;
    }
</style>