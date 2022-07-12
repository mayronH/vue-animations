<script setup lang="ts">
import { ref } from 'vue'

const showP = ref(false)
</script>

<template>
  <div class="content">
    <transition name="fade">
      <div v-if="showP">hello there</div>
    </transition>
    <button @click="showP = !showP">Toggle</button>
  </div>
</template>

<style scoped>
.content {
  text-align: center;
}
/* the start of the animation when the element is entering the DOM  */
.fade-enter-from {
  opacity: 0;
}
/* the end of the animation */
/* we don't need the enter-to, opacity 1 is the default behavior */
/* .fade-enter-to {
  opacity: 1;
} */
/* control the transition */
.fade-enter-active {
  transition: opacity 2s ease;
}

/* the start of the animation when the element is leaving the DOM */
/* .fade-leave-from {
  opacity: 1;
} */
/* the end of the animation */
.fade-leave-to {
  opacity: 0;
}
/* control the transition */
.fade-leave-active {
  transition: opacity 2s ease;
}
</style>
