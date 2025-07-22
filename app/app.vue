<script setup lang="ts">
import { VaporComponent, VanillaComponent } from '#components'

const displayVapor = ref(true)
</script>

<template>
  <div class="container">
    <div>
      <button type="button" class="btn btn-primary btn-block" @click="displayVapor = !displayVapor">
        {{ displayVapor ? 'Switch to normal Vue component' : 'Switch to Vue Vapor component' }}
      </button>
    </div>
    <component :is="displayVapor ? VaporComponent : VanillaComponent" />
  </div>
</template>

<style scoped>
div {
  background-color: #eee;
  padding: 1rem;
  
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
