<template>
  <v-toolbar fixed class="cyan" dark>
    <v-toolbar-title class="mr-4">
      <span
        class="home"
        @click="navigateTo({name: 'hello'})">
          TabTracker
      </span>
    </v-toolbar-title>

    <v-toolbar-items>
      <v-btn flat dark
        @click="navigateTo({name: 'hello'})">
        Browse
      </v-btn>
    </v-toolbar-items>

    <v-spacer></v-spacer>

    <v-toolbar-items
      v-if="!$store.state.isUserLoggedIn">
        <v-btn flat dark
          @click="navigateTo({name: 'Login'})">
            Login
        </v-btn>
    </v-toolbar-items>

    <v-toolbar-items
      v-if="!$store.state.isUserLoggedIn">
        <v-btn flat dark
          @click="navigateTo({name: 'Register'})">
            Sign-Up
        </v-btn>
    </v-toolbar-items>
  </v-toolbar>
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  }
}
</script>

<style scoped>
.home {
  cursor: pointer;
}
.home:hover {
  color: black;
}
</style>
