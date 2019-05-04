<template>
    <v-app>
        <v-toolbar app>
            <v-toolbar-title class="headline text-uppercase">
                <span>GYUDON</span>
                <span class="font-weight-light">PURCHASE</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn
                    flat
                    href="https://github.com/vuetifyjs/vuetify/releases/latest"
                    target="_blank"
            >
                <span class="mr-2">Latest Release</span>
            </v-btn>
        </v-toolbar>
<!---->
        <v-content>
            <MainShow/>
        </v-content>
    </v-app>
</template>

<script>
    import MainShow from "@/components/MainShow";

    export default {
        name: 'App',
        components: {
            MainShow,
        },
        data() {
            return {
                //
            }
        }
    }
</script>
