<template>
    <div class="indexContainer">
       
        <!--<div class="show"> {{msg}}</div>-->
    
        <div class="editorContainer">
            <markdown v-bind:mdValues.sync="msg" @childevent="childEventHandler"></markdown>
        </div>
    </div>
</template>

<script>
    import markdown from '../components/markdown'
    export default {
        name: 'index',
        data() {
            return {
                msg: '## Vue-markdownEditor'
            }
        },
        components: {
            markdown
        },
        methods: {
            childEventHandler:function(res){
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