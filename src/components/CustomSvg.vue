<script setup>
import { gsap } from "gsap"
import { GSDevTools } from "gsap-trial/all";
import { onMounted, ref } from "vue";

gsap.registerPlugin(GSDevTools)

const svg = ref(null)

const animation = gsap.timeline({
  defaults: {
    duration: 1,
    ease: "bounce"
  },
  repeat: -1,
  repeatDelay: 1,
})

onMounted(() => {
  animation.to("polyline", {
    attr: {
      points: "0.1 0.5 0.5 0.5 0.9 0.5"
    }
  })
    .to("polyline", {
      attr: {
        points: "0.1 0.5 0.5 0.9 0.9 0.5"
      },
      delay: 0.3
    })
    .to("polyline", {
      attr: {
        points: "0.5 0.5 0.5 0.1 0.5 0.5"
      },
      ease: "linear",
      duration: 0.3,
      delay: 0.3
    })

  GSDevTools.create({ animation })
})
</script>

<template>
  <svg class="mySvg" ref="svg" clipPathUnits="objectBoundingBox" viewBox="0 0 1 1" xmlns="http://www.w3.org/2000/svg">
    <!-- <circle class="c1" r="0.3" cx="0.5" cy="0.5" />
    <circle class="c2" r="0.3" cx="0.5" cy="0.5" /> -->
    <polyline points="0.5 0.1 0.5 0.5 0.5 0.1" />
  </svg>
</template>

<style scoped>
svg.mySvg {
  width: 500px;
  height: 500px;
  border: 1px solid white;
}

circle {
  fill: #00b500;
}

polyline {
  stroke: limegreen;
  stroke-width: 0.01;
  fill: none;
}
</style>