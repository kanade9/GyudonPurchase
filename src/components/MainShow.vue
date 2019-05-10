<template>
    <div>
        <!--<p>-->
        <!--This is MainShow-->
        <!--</p>-->
        <!--<h4>This page will be a top page</h4>-->
        <!--<br>-->
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
                        <app-menu-button menu="漬物" N=2 S=1 O=0 A=100 @tellValue="addList"></app-menu-button>
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
                <v-flex xs3>
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

        <v-container grid-list-md text-xs-center>
            <v-layout row reverse wrap>
                <!--<v-layout justify-center>-->
                <v-flex xs6 sm3>
                    <p>
                        <v-btn color="success" v-on:click="judge()">値段を計算する</v-btn>
                    </p>
                    <h1>小計 {{total_value}}円</h1>
                    <h1>割引額{{discount}}円</h1>
                    <h1>合計{{sum_value}}円</h1>
                </v-flex>
                <v-flex xs6 sm3>
                    <div v-for="i in order"
                         v-bind:key="i.id"
                         v-bind:class="{highValue: i.N > 500 }">
                        <h3>{{ i.name }}</h3>
                        <!--{{ i.N }} {{ i.S }} {{ i.O }} {{ i.A }}-->
                    </div>
                </v-flex>
                <v-flex xs12 sm6>
                    <app-carousels></app-carousels>
                </v-flex>

            </v-layout>
        </v-container>
    </div>
</template>

<script>
    import AppMenuButton from "@/components/AppMenuButton";
    import AppCarousels from "@/components/AppCarousels";

    const ev = [110, 111, 200, 210, 212, 300, 310, 401, 402];
    const acception = [false, false, true, false, true, true];
    const status_table = [
        [2, 1, -1, -1, -1, -1, -1, -1, -1],
        [-1, -1, -1, -1, -1, -1, -1, 2, -1],
        [-1, -1, 2, 4, 3, 5, 5, -1, -1],
        [-1, -1, -1, -1, -1, -1, -1, -1, 4],
        [-1, -1, 4, 4, 3, 4, 5, -1, -1],
        [-1, -1, -1, -1, -1, 5, 5, -1, -1],
    ];

    function get_event_index(code) {
        // alert(code);
        for (let i = 0; i < 9; i++) {
            if (ev[i] === code) {
                return i;
            }
        }
    }

    export default {
        name: "ShowCase",
        components: {AppCarousels, AppMenuButton},
        data: function () {
            return {
                total_value: 0,
                discount: 0,
                sum_value: 0,
                order: [
                    {name: '購入リスト', N: 0, S: 0, O: 0, A: 0}]
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
                let accepted = false;
                let event_code = 0;
                let event_index = 0;

                for (let i = 1; i <= order_count; i++) {
                    amount += parseInt(this.order[i].A);

                    event_code = parseInt(this.order[i].N) * 100 + parseInt(this.order[i].S) * 10 + parseInt(this.order[i].O);
                    event_index = get_event_index(event_code);
                    // alert(event_index);

                    // 割引額の設定
                    if (status === 4 && event_index === 6) {
                        this.discount += 50;
                    }

                    status = status_table[status][event_index];

                    this.total_value = amount;

                    this.sum_value = this.total_value - this.discount;

                    // alert(status);
                    if (status === -1) {
                        alert('error! please retry');
                        location.reload();
                    }
                }
                if (status === -1) {
                    accepted = false;
                } else {
                    accepted = acception[status];
                }

                if (accepted) {
                    alert('購入可')
                } else {
                    alert('購入不可')
                }
            },
        }
    }

</script>

<style scoped>

</style>
