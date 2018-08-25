<template>
    <div>
        <h2>{{title}} --- {{homemsg}}</h2>
        <button @click="run('123')">执行父组件的方法</button>
        <button @click="getParnt()">获取父组件的数据和方法</button>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                msg: '子组件的msg'
            }
        },
        methods: {
            getParnt(){
                this.home.run('456')
            }
        },
        props: ['title', 'homemsg', 'run', 'home']
    }
</script>

<style lang="scss" scoped>

</style>
