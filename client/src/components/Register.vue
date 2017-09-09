<template>
<div>
  <h1>Register</h1>
  
  <input
    type="email"
    name="email"
    v-model="email"
    placeholder="email" />
    <br/>
  <input
    type="password"
    name="pasword"
    v-model="password"
    placeholder="password" />
  <br>
  <button
    @click="register"
  >Register</button>
</div>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: ''
    }
  },
  watch: {
    email (value) {
      console.log('email has changed', value)
    }
  },
  methods: {
    async register () {
      await AuthenticationService.register({
        email: this.email,
        password: this.password
      })
    }
  },
  mounted () {
    setTimeout(() => {
      this.email = 'hello world'
    }, 1000)
  }
}
</script>

<style scoped>

</style>
