<template>
    <div>
        <form @submit.prevent="register">
          <label for="name">
            Name:
          </label>
          <input v-model="name" type="text" name="name" value>
    
          <label for="email">
            Email:
          </label>
          <input v-model="email" type="email" name="email" value>
    
          <label for="password">
            Password:
          </label>
          <input v-model="password" type="password" name value>
    
          <button type="submit" name="button">
            Register
          </button>

          <p>{{errors}}</p>

          <router-link to="/login">
            Already Have an Account? Login!
          </router-link>
        </form>
      </div>
</template>

<script>
    export default {
        data() {
            return {
                name: '',
                email: '',
                password: '',
                errors: null
            }
        },
        methods: {
            register() {
                this.$store.dispatch('register', {
                    name: this.name,
                    email: this.email,
                    password: this.password
                })
                .then(() => {
                    this.$router.push({name: 'dashboard'})
                })
                .catch(err => {
                  this.errorr = err.response.data
                })
            }
        }
    }
</script>

<style  scoped>

</style>