<template>
  <v-layout column>
    <v-flex xs6 offset-xs3>
      <div class="white elevation-2">
        <v-toolbar flat dense class="cyan" dark>
          <v-toolbar-title>Login</v-toolbar-title>
        </v-toolbar>

          <div class="pl-4 pr-4 pt-2 pb-2"> 
            <v-text-field
              label="Email"
              type="email"
              name="email"
              v-model="email"
              required>
              </v-text-field>
            <br/>
            <v-text-field
              label="Password"
              type="password"
              name="pasword"
              v-model="password"
              required>
            </v-text-field>
            <br>
            <div class= "error" v-html="error" />
            <v-btn
              class="cyan"
              @click="login"
              dark>Login</v-btn>
        </div>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  watch: {
    email (value) {
      console.log('email has changed', value)
    }
  },
  methods: {
    async login () {
      try {
        const response = await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<style scoped>
  .error {
    color: red;
  }
</style>
