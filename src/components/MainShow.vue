<template>
    <div>
        <p>
            This is MainShow
        </p>
        <h4>This page will be a top page</h4>
        <br>
        <v-container grid-list-md text-xs-center>
        <v-layout justify-center>
        <v-flex xs3>
        <h3>メインメニュー</h3>
        <p>
            <app-menu-button menu="牛丼" N=1 S=1 O=1 A=380 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="豚丼" N=1 S=1 O=1 A=350 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="鮭定食" N=1 S=1 O=0 A=450 @tellValue="addList"></app-menu-button>
        </p>
        </v-flex>
            <v-flex xs3>
        <h3>サイドメニュー1</h3>
        <p>
            <app-menu-button menu="野菜サラダ" N=2 S=1 O=2 A=100 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="ポテトサラダ" N=2 S=1 O=2 A=130 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="漬物" N=2 S=1 O=2 A=100 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="生卵" N=2 S=0 O=0 A=60 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="温泉卵" N=2 S=0 O=0 A=70 @tellValue="addList"></app-menu-button>
        </p>
            </v-flex>
            <v-flex xs3>
        <h3>サイドメニュー2</h3>
        <p>
            <app-menu-button menu="みそ汁" N=3 S=1 O=0 A=60 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="豚汁" N=3 S=0 O=0 A=190 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="スープ" N=3 S=1 O=0 A=200 @tellValue="addList"></app-menu-button>
        </p>
            </v-flex>
            <v-flex xd3>
        <h3>オプション</h3>
        <p>
            <app-menu-button menu="並" N=4 S=0 O=1 A=0 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="大盛り" N=4 S=0 O=1 A=100 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="特盛" N=4 S=0 O=1 A=200 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="ごまドレッシング" N=4 S=0 O=2 A=0 @tellValue="addList"></app-menu-button>
        </p>
        <p>
            <app-menu-button menu="和風ドレッシング" N=4 S=0 O=2 A=0 @tellValue="addList"></app-menu-button>
        </p>
            </v-flex>
        </v-layout>
        </v-container>
        <ul>
            <li v-for="i in order"
                v-bind:key="i.id"
                v-bind:class="{ tuyoi: i.hp > 300 }">
                {{ i.name }} {{ i.N }} {{ i.S }} {{ i.O }} {{ i.A }}
            </li>
        </ul>
        <p>
            <button v-on:click="judge()">値段を計算する</button>
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
            judge: function () {
                let order_count = this.order.length - 1;
                let status = 0;
                let amount = 0;
                let discount = 0;
                let accepted = false;

                for (let i = 1; i <= order_count; i++) {
                    amount += parseInt(this.order[i].A);
                    this.totalvalue = amount;
                    // alert(value);
                }

                // for (let i = 0; i < this.order.length; i++) {
                //     amount += parseInt(this.order[i].A);
                // }
                // this.totalvalue = amount;
                // alert(value);
            },
        }
    }

</script>

<style scoped>

</style>
