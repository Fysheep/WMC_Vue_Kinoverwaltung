<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <nav>
    <RouterLink to="/" class="rLink">Übersicht</RouterLink>
    <span class="horizontalSpacer"></span>
    <img src="" alt="Logo" class="navImg">
  </nav>
  <div id="navSpacer" />

  <div id="CONTENT">
    <RouterView />
  </div>

  <footer>

  </footer>
</template>

<style scoped>
nav {
  display: flex;
  column-gap: 1rem;
  box-shadow: 0px 0px 10px black;
  background-color: var(--bg);
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: fit-content;
  padding: 1rem;
}

#navSpacer {
  height: 4rem;
}

.rLink {
  height: fit-content;
  text-decoration: none;
  color: var(--outline-color);
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-size: x-large;
}

.navImg {
  max-height: 3rem;
  min-width: 2rem;
  margin: -0.7rem;
}

.horizontalSpacer {
  width: calc(100%);
  max-width: calc(100% - 13rem);
}
</style>