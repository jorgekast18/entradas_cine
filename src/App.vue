<template>
  <div id="app" class="principal">
    <span>{{ title }}</span>
    <div>
      <button @click="currentComponent = item.name" v-for="(item, index) in menu" :key="index" class="menu"> {{ item.description }}</button>
    </div>
    <component :is="currentComponent"></component>
  </div>
</template>

<script>
import Entrada from '@/views/Entrada'
import Home from '@/views/Home.vue'
import Login from '@/views/user/Login.vue'
import Profile from '@/views/user/Profile.vue'
import Register from '@/views/user/Register.vue'

export default {
  components: { Entrada, Home, Profile, Login, Register },
  name: 'App',
  data () {
    return {
      title: 'Entradas',
      currentComponent: 'entrada',
      menu: [
        { description: 'Home', name: 'home'},
        { description: 'Entradas', name: 'entrada'},
        { description: 'Perfil', name: 'profile'},
        { description: 'Login', name: 'login'},
        { description: 'Registro', name: 'register'},
      ]
    }
  }
}
</script>

<style>

html {
  font-size: 62.5% !important;
}

.menu {
  color: white;
  background-color: transparent;
  font-weight: normal;
  font-size: 1.8rem;
  margin: 3px 2px;
}
.principal {
  background-color: red;
  padding: 10px;
  color: white;
  border-radius: 5px;
  width: 400px;
  font-size: 3rem;
  text-align: center;
}

a {
    text-decoration: none;
    color: purple
}

button {
  background-color: #552f75;
  color: white;
  font-size: 2.4rem;
  font-weight: bold; 
  border-style: none;
  border-radius: 5px;
  padding: 3px 10px;
  margin: 3px 5px;
  min-width: 35px;
  cursor: pointer;
}

button:focus {
  outline: 0;
}

input[type='text'] {
  border-radius: 5px;
  font-size: 2.4rem;
  width: 100%;
  line-height: 4rem;
  padding: 3px;
}
</style>

