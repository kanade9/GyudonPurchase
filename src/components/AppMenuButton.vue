<template>
    <!--<v-container>-->
    <v-layout justify-center>
        <v-card class="pa-0 ma-0">
            <v-card-actions>
                <v-btn flat color="red" type="button" v-on:click='tell()'>
                    <!--<span style=" color: #333399; ">{{menu}}</span>-->
                    <!--<span style=" color: brown">{{A}}円</span>-->
                    <p id="tag">{{menu}}<br>{{A}}円<br></p>
                </v-btn>
            </v-card-actions>
        </v-card>
    </v-layout>
    <!--</v-container>-->
</template>

<script>
    export default {
        name: "AppMenuButton",
        props: ['menu', 'N', 'S', 'O', 'A'],
        data: function () {
            return {}
        },
        methods: {
            tell: function () {
                this.$emit('tellValue', this.menu, this.N, this.S, this.O, this.A)
            }
        }
    }
</script>

<style scoped>
    #tag {
        color: darkblue;
        font-weight: bold;
        font-size: 100%;
    }
</style>
