<script setup>
import { onMounted, ref } from 'vue';
import { gsap } from "gsap"
import { TextPlugin } from "gsap/TextPlugin"

gsap.registerPlugin(TextPlugin)

const paragraph = ref(null)

onMounted(() => {
  gsap.to(paragraph.value, {text: "Hello TextPlugin from GSAP", ease: "none", duration: 2})
})
</script>

<template>
<p ref="paragraph"></p>
</template>

<style scoped>
  @font-face {
  font-family: "MyFont";
  font-style: normal;
  font-weight: 400;
  src: url("./assets/fonts/TheRiversRegular.otf") format("opentype");
  font-display: swap;
}

  body{
    height: 100vh;
    background-color: #333;
    color: white;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: "MyFont", Arial, sans-serif;
    font-size: 2vw;
  }
</style>
