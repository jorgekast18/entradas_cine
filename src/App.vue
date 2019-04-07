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
</style>

