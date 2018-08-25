<template>
    <div id="home">
        <v-header :title="title" :run="run" :homemsg="msg" :home="this"></v-header>
        <hr>
        首页组件
    </div>
</template>
<script>
    import Header from './Header.vue';

    export default {
        data(){
            return {
                msg: '我是一个home组件',
                title: '首页111'
            }
        },
        methods: {
            run(data){
                alert('run方法'+data)
            }
        },
        components: {
            'v-header': Header
        }
    }
</script>
<style lang="scss" scoped>

</style>
