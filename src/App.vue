<template>
  <div id="app" class="principal">
    <span>{{ title }}</span>
    <Entrada/>
  </div>
</template>

<script>
import Entrada from '@/views/Entrada'
export default {
  components: { Entrada },
  name: 'App',
  data () {
    return {
      title: 'Entradas'
    }
  }
}
</script>

<style>

html {
  font-size: 62.5% !important;
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

.button {
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

input[type='text'] {
  border-radius: 5px;
  font-size: 2.4rem;
  width: 100%;
  line-height: 4rem;
  padding: 3px;
}
</style>

