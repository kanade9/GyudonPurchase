<template>
    <div>
        <p>
            This is MainShow
        </p>
        <h4>This page will be a top page</h4>
        <p>
            <app-menu-button menu="牛丼" N=1 S=1 O=1 A=380 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="豚丼" N=1 S=1 O=1 A=350 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="鮭定食" N=1 S=1 O=0 A=450 @tellValue="addList"></app-menu-button>
        </p>
        <ul>
            <li v-for="i in order"
                v-bind:key="i.id"
                v-bind:class="{ tuyoi: i.hp > 300 }">
                {{ i.name }} {{ i.N }} {{ i.S }} {{ i.O }} {{ i.A }}
            </li>
        </ul>
        <p>
            <button v-on:click="sum()">値段を計算する</button>
        </p>
        <h1>合計 {{totalvalue}}円</h1>
    </div>
</template>

<script>
    import AppMenuButton from "@/components/AppMenuButton";

    export default {
        name: "ShowCase",
        components: {AppMenuButton},
        data: function () {
            return {
                totalvalue: 0,
                order: [
                    {name: 'init', N: 0, S: 0, O: 0, A: 0}]
            }
        },
        methods: {
            addList: function (menu, group, set, option, price) {
                // リストに追加
                this.order.push({
                    name: menu, N: group, S: set, O: option, A: price
                    // alert(menu + ' is selected ID=' + array2);
                })
            },
            sum: function () {
                let value = 0;
                for (let i = 0; i < this.order.length; i++) {
                    value += parseInt(this.order[i].A);
                }
                this.totalvalue = value;
                // alert(value);
            },
        }
    }

</script>

<style scoped>

</style>
