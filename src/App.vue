<template>
  <v-app id="app">    
    <Navigation/>
    <router-view/>
  </v-app>
</template>

<script>
import Navigation from '@/components/Navigation'

export default {
    
    components: {
        Navigation
    },   
    mounted() {
      //console.log(this);
    }
}
</script>
