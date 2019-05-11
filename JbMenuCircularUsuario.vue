<template>
    <v-menu offset-y :close-on-content-click="false" class="mx-1" min-width="200">
        <v-badge overlap slot="activator" color="deep-orange" >
            <v-avatar size="30" color="grey lighten-4" >
                <v-icon color="primary" size="20">person</v-icon>
            </v-avatar>
        </v-badge>
            
        <v-list class="menu_circular_usuario">
            <template>
                <v-list-tile v-if="titulo">
                    <v-list-tile-title class="font-italic text-capitalize font-weight-bold" >{{titulo}}</v-list-tile-title>
                </v-list-tile>

                <v-list-tile href="/changePassword">
                    <v-icon>lock</v-icon>
                    <v-list-tile-title>Senha</v-list-tile-title>
                </v-list-tile>

                <!-- efetua logout -->
                <v-list-tile @click="logout" >
                    <v-icon>exit_to_app</v-icon>
                    <v-list-tile-title>Sair</v-list-tile-title>
                </v-list-tile>
            </template>
        </v-list>                    
    </v-menu>
</template>

<script>
    export default {
        props:{
            csrf:String, 
            logoutHref:String, titulo:String,
        },
        data: function(){
            return {

            }
        },
         methods: {
            logout(e){
                var form = document.createElement("form");
                var csrf = document.createElement("input"); 

                form.method = "POST";
                form.action = this.logoutHref;   
                form.id = "logout-form";   

                csrf.value=this.csrf;
                csrf.name="_token";
                csrf.type="hidden";
                form.appendChild(csrf);  

                document.body.appendChild(form);

                form.submit();
            }
        },
        mounted() {
        }
    }
</script>

<style>
.menu_circular_usuario a:hover{
    text-decoration: none;
    color: #212529 !important;
}
</style>
