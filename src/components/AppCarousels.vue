<template>
    <v-card title>
        <!--<v-carousel height="400px" >-->
        <!--style="width:460px;height:400px"-->
        <!--<v-carousel-item v-for="(carousel,i) in carousels" v-bind:src="carousel.src"-->
        <!--:key="i"></v-carousel-item>-->
        <!--<v-carousel-item v-for="(carousel,i) in carousels" v-bind:src="carousel.src"-->
        <!--:key="i"></v-carousel-item>-->
        <v-img
                :src="`https://user-images.githubusercontent.com/47267817/57549129-b083d400-739d-11e9-9f7c-1f9f7016ba43.png`"
                aspect-ratio="1.1"
                class="grey lighten-2"
        >
        </v-img>
        <!--<h2>購入に関しての注意事項</h2><br>-->

        <!--</v-carousel>-->
        <v-card text>
            <h3>購入に関しての注意事項</h3><br>
            <p id="caution">牛丼、豚丼はサイズをサラダはドレッシングを必ず選んでください<br>
            必ずメインメニューから一品だけ購入してください。メイン二品以上はエラーになります<br>
            必ずメイン、サイド１、サイド２の順番で購入してください<br>
            サイド1,2は何品でも購入することができます
            </p>
        </v-card>
    </v-card>
</template>

<script>
    export default {
        name: "AppCarousels",
        data: function () {
            return {
                carousels: [
                    {src: 'https://user-images.githubusercontent.com/47267817/57549129-b083d400-739d-11e9-9f7c-1f9f7016ba43.png'},
                    {src: 'https://user-images.githubusercontent.com/47267817/57548936-2f2c4180-739d-11e9-8f4d-ce1363c707a6.png'},

                ]
            }
        },
    }
</script>

<style scoped>
#caution{
    border: solid 3px coral;
    font-family: "Apple Chancery",serif;
    font-weight: bolder;
    font-size: 130%;
    color:red;


}
</style>
