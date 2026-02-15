<script setup>
import HeroComponent from "./components/HeroComponent.vue";
import NavbarComponent from "./components/NavbarComponent.vue";
</script>

<template>
  <div  id="inicio"  class="container">
    <NavbarComponent />
    <HeroComponent />
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  min-height: 100dvh;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}
</style>
