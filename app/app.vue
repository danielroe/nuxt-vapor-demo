<script setup lang="ts">
import { VaporComponent, VanillaComponent } from '#components'

const displayVapor = ref(false)
</script>

<template>
  <div>
    <button @click="displayVapor = !displayVapor">
      {{ displayVapor ? 'Show Non-vapor Component' : 'Show Vapor Component' }}
    </button>
  </div>
  <component :is="displayVapor ? VaporComponent : VanillaComponent" />
</template>

<style scoped>
div {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  
  gap: 2rem;
}
</style>

<style>
@import './css/bootstrap.min.css';

body {
    padding: 10px 0 0 0;
    margin: 0;
    overflow-y: scroll;
}
#duration {
    padding-top: 0px;
}
.jumbotron {
    padding-top:10px;
    padding-bottom:10px;
}
.test-data a {
    display: block;
}
.preloadicon {
    position: absolute;
    top:-20px;
    left:-20px;
}
.col-sm-6.smallpad {
    padding: 5px;
}
.jumbotron .row h1 {
    font-size: 40px;
}
</style>
