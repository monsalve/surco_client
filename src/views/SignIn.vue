<template>
    <form @submit.prevent="submit">        
        <div>
            <label for="email">Email</label>
            <input type="text" name="email" id="email" v-model="form.email">
        </div>
        <div>
            <label for="email">Contraseña</label>
            <input type="password" name="password" id="password" v-model="form.password">
        </div>
        <div>
            <button type="submit">Ingresar</button>
        </div>
    </form> 
</template>
 
<script>
import { mapActions } from 'vuex'

export default {
    //props : ['ruta'],    
    name: 'signin',
    components: {
        
    },
  
    data() {
        return {
            form: {
                email: '',
                password: '',
            }
        }
    },

    methods: {
        ...mapActions({
            signIn: 'auth/signIn'
        }),
        submit () {
          this.signIn(this.form).then(() => {
              this.$router.replace({
                  name: 'dashboard'
              })
          }).catch(() => {
              console.log('fail login');
          })
        }
    },



}
</script>
