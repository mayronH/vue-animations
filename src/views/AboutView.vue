<template>
  <div class="content about">
    <!-- Javascript hooks -->
    <transition
      name="fade"
      appear
      @before-enter="beforeEnter"
      @enter="enter"
      @after-enter="afterEnter"
      @before-leave="beforeLeave"
      @leave="leave"
      @after-leave="afterLeave"
    >
      <h1 v-if="showTitle">About</h1>
    </transition>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a dolore consequatur
      assumenda nam!
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a dolore consequatur
      assumenda nam!
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Cum aperiam
      officia possimus delectus inventore quod quisquam culpa voluptas iusto,
      quae maiores quo dolorum, corporis laboriosam a dolore consequatur
      assumenda nam!
    </p>
  </div>
</template>

<script setup lang="ts">
import { ref, RendererElement } from 'vue'
import gsap from 'gsap'

const showTitle = ref(true)

function beforeEnter(el: RendererElement) {
  console.log('before enter', el)
  el.style.transform = 'translateY(-60px)'
  el.style.opacity = '0'
}
function enter(el: RendererElement, done: () => void) {
  console.log('enter', el)
  gsap.to(el, {
    y: 0,
    opacity: 1,
    duration: 2,
    ease: 'bounce.out',
    // without onComplete: done, Vue doesn't know when the animation is done so the afterEnter is triggered immediately
    onComplete: done,
  })
}
function afterEnter(el: RendererElement) {
  console.log('after enter', el)
  // el.style.color = 'green'
  // setTimeout(() => (showTitle.value = false), 2000)
}
function beforeLeave(el: RendererElement) {
  // el.style.color = 'pink'
  console.log('before leave', el)
}
function leave(el: RendererElement) {
  console.log('leave', el)
}
function afterLeave(el: RendererElement) {
  console.log('after leave', el)
}
</script>

<style scoped>
.about {
  max-width: 600px;
  margin: 20px auto;
}
/* 
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 1s ease;
} */
</style>
