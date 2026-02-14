<script setup>
import HeroComponent from "./components/HeroComponent.vue";
import NavbarComponent from "./components/NavbarComponent.vue";
</script>

<template>
  <div class="container">
    <NavbarComponent />
    <HeroComponent />
  </div>
</template>

<style scoped>
.container {
  width: 100%;
  height: 100dvh;
  display: grid;
  place-items: center;
  position: relative;
}
</style>
