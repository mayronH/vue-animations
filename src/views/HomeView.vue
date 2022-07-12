<script setup lang="ts">
import { ref } from 'vue'
import Toast from '../components/ToastComponent.vue'
import Todo from '../components/TodoComponent.vue'

const showToast = ref(false)
const triggerToast = () => {
  showToast.value = true
  setTimeout(() => (showToast.value = false), 3000)
}
</script>
<template>
  <div class="content">
    <transition name="toast">
      <Toast v-if="showToast" />
    </transition>
    <Todo @bad-value="triggerToast" />
  </div>
</template>

<style>
/* .toast-enter-from {
  opacity: 0;
  transform: translateY(-100px);
} */
/* .toast-enter-to {
  opacity: 1;
  transform: translateY(0);
} */
.toast-enter-active {
  /* transition: opacity 0.8s ease, transform 0.4s ease; */
  animation: wobble 0.6s ease;
}
/* CUSTOM CSS Animation */
@keyframes wobble {
  0% {
    opacity: 0;
    transform: translateY(-100px);
  }
  50% {
    opacity: 1;
    transform: translateY(0);
  }
  60% {
    transform: translateX(8px);
  }
  70% {
    transform: translateX(-8px);
  }
  80% {
    transform: translateX(4px);
  }
  90% {
    transform: translateX(-4px);
  }
  100% {
    transform: translateX(0);
  }
}

/* .toast-leave-from {
  opacity: 1;
} */
.toast-leave-to {
  opacity: 0;
}
.toast-leave-active {
  transition: opacity 0.3s ease;
}
</style>
