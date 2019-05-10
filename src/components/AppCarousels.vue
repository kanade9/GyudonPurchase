<template>
    <!--<v-card class="pa-3">-->
        <!--<v-carousel>-->
            <!--<v-carousel-item v-for="(carousel,i) in carousels" v-bind:src="carousel.src" :key="i"></v-carousel-item>-->
        <!--</v-carousel>-->
    <!--</v-card>-->
    <img src="https://github.com/kzmaro/GyudonPurchase/blob/pic/menu.png" alt="" width="" height="" border="0" />
</template>

<script>
    export default {
        name: "AppCarousels",
        data: function () {
            return {
                carousels: [
                    {src: 'https://github.com/kzmaro/GyudonPurchase/blob/pic/menu.png'},
                    {src: 'https://github.com/kzmaro/GyudonPurchase/blob/pic/careful.png'},

                ]
            }
        },
    }
</script>

<style scoped>

</style>
