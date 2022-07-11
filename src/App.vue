<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
</script>

<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/contact">Contact</router-link>
  </div>
  <router-view />
</template>

<style>
#app {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  min-height: 100vh;
}
.content {
  flex: 1;

  width: 100%;
}
.content h1 {
  text-align: center;
}
#nav {
  padding: 30px;
}
#nav a {
  font-weight: bold;
  color: var(--white);
}
#nav a.router-link-exact-active {
  color: var(--accent2);
}
</style>
