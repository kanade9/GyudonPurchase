<template>
    <v-carousel height="400px">
        <v-carousel-item style="width:100%;height:400px" v-for="(carousel,i) in carousels" v-bind:src="carousel.src"
                         :key="i"></v-carousel-item>
    </v-carousel>
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

</style>
