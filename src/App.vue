<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'

</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo_minero.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="Proyecto Mineros" />

      <nav>
        <RouterLink class="item" to="/">Inicio</RouterLink>
        <a href="webcam.html" class="item" to="/camara" target="_blank">Cámara</a>
      </nav>
    </div>
  </header>
  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto;  
}

.nav{
  display: block;
  margin: 0 auto;  
}

.item{
  margin: 3px;
  color: white;
}

.item:hover{
  color: #41b883;
}

</style>
