<template>
    <v-list-tile :href="href">
        <v-icon class="mr-1">{{icone}}</v-icon>
        <v-list-tile-title>{{titulo}}</v-list-tile-title>
    </v-list-tile>
</template>

<script>
    export default {
        props:{
            titulo:String,
            href:String, icone:String
        },
        data(){return {
        }},
        
    }
</script>

<style>
.menu_circular_usuario a:hover{
    text-decoration: none;
    color: #212529 !important;
}
</style>
