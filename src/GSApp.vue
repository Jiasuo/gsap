<script setup>
import {gsap} from "gsap"
import { onMounted } from "vue";

onMounted(() => {
  gsap.from(".hi", {
    y: -300,
    ease: "bounce",
    duration: 2
  })
})
</script>

<template>
<div class="body">
  <h1 class="hi">Hello world</h1>
</div>
</template>

<style>
.body{
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Poppins", arial, sans-serif;
}
</style>
