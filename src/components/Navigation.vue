<template>
    <v-app id="inspire">
        <v-app-bar :clipped-left="$vuetify.breakpoint.lgAndUp" app color="blue-grey darken-3" dark >
            <v-app-bar-nav-icon v-if="authenticated"  @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
            <v-toolbar-title style="width: 300px"  class="ml-0 pl-4">
                <span class="hidden-sm-and-down">Surcoestudios</span>
            </v-toolbar-title>
            <v-spacer></v-spacer>
            <v-btn text @click.prevent="navegar('Home')">Inicio
                <!-- <router-link 
                    :to="{ name: 'Home'}"
                >Home</router-link>-->
            </v-btn>
            <v-btn text @click.prevent="navegar('Home')">Inicio</v-btn>
            <v-btn v-if="authenticated" icon @click.prevent="signOut">
                Salir               
            </v-btn>
        </v-app-bar>
        
        <ul>
            <li>            
                <router-link 
                    :to="{ name: 'Home'}"
                >Home</router-link>
            </li>
            <li>            
                <router-link 
                    :to="{ name: 'prueba'}"
                >Prueb</router-link>
            </li>
            
            <template v-if="authenticated">
                <li>
                {{ user.name }}
                </li>
                <li>
                    <router-link 
                        :to="{ name: 'dashboard'}"
                    >Dashboard</router-link>
                </li>        
                <li>
                    <a href="#" @click.prevent="signOut">Salir</a>
                </li>
            </template>
            <template v-else>
                <li>
                    <router-link 
                        :to="{ name: 'signin'}"
                    >Ingresar</router-link>
                </li>
            </template>
        </ul>
    </v-app>
</template>

<script>
    import { mapGetters, mapActions } from 'vuex'
    export default {    
        computed: {
           ...mapGetters({
               authenticated: 'auth/authenticated',
               user: 'auth/user'
           })
        },
        data: () => ({
            dialog: false,
            drawer: null,
        }),
       methods: {
           ...mapActions({
               signOutAction: 'auth/signOut'
           }),
           
           signOut () {
               this.signOutAction().then(() => {
                   this.$router.replace({
                       name: 'home'
                   })
               })
              
           },

           navegar (rutaNav) {
                this.$router.replace({
                    name: rutaNav
                })
           }
       }
       
    }
</script>

<style scoped>
 
</style>


