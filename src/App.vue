<template>
  <v-app>
    <v-toolbar color="primary" dark app>
      <v-toolbar-title class="headline text-uppercase">
        <span>{{ title }}</span>
      </v-toolbar-title>
    </v-toolbar>

    <v-content>
      <v-container fluid fill-height>
        <component :is="currentComponent"></component>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Home from '@/views/Home.vue'
import Register from '@/views/user/Register.vue'
import Login from '@/views/user/Login.vue'
import Profile from '@/views/user/Profile.vue'
export default {
  components: { Home, Register, Login, Profile },
  name: 'App',
  data () {
    return {
      title: 'Súper Ópera',
      currentComponent: 'home'
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Great+Vibes');
</style>
