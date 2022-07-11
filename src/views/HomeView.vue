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
    <Toast v-if="showToast" />
    <Todo @bad-value="triggerToast" />
  </div>
</template>

<style></style>
