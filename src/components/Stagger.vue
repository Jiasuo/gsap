<script setup>
  import { onMounted, ref } from 'vue';
  import {gsap} from "gsap"
  import { SplitText, GSDevTools } from 'gsap-trial/all';

  gsap.registerPlugin(SplitText, GSDevTools)

  const staggerAmount = 0.5

  let animation = gsap.timeline({repeat: -1})

  const container = ref(null)

  onMounted(() => {
    // DOM elements
    const divs = container.value.querySelectorAll("div")
    // Set opacity
    gsap.set(container.value, {autoAlpha: 1})
    gsap.set(divs, {transformOrigin: "50% 50% -50"})
    // Set animation
    animation.from(divs, {
      rotationX: -90,
      opacity: 0,
      stagger: {
        each: staggerAmount
      },
      // duration: 1,
    })
    .to(container.value.querySelectorAll("div"), {
      rotationX: 90,
      opacity: 0,
      stagger: staggerAmount
    }, staggerAmount)

    // Dev tools
    GSDevTools.create({animation})
  })
</script>

<template>
  <div class="container" ref="container">
    <div class="text n">Bonjour</div>
    <div class="text n">Je</div>
    <div class="text n">Suis</div>
    <div class="text n">Ton</div>
    <div class="text n">Père</div>
  </div>
</template>

<style>
  .container{
    position: relative;
    text-align: center;
    perspective: 400px,
  }
  .text{
    position: absolute;
  }
</style>