<template>
    <button type="button" v-on:click='tell()'>
        <span style="font-size: large; color: #333399; ">{{menu}}</span>
    </button>
</template>

<script>
    export default {
        name: "AppMenuButton",
        props: ['menu','N','S','O','A'],
        data: function(){
            return{}
        },
        methods:{
            tell: function(){
                this.$emit('tellValue',this.menu,this.N,this.S,this.O,this.A)
            }
        }
    }
</script>

<style scoped>

</style>
