<script setup>
  import {gsap} from "gsap"
import { onMounted, ref } from "vue";

const faces = ref(null)

  onMounted(() => {
    const anim = gsap.to(faces.value, {rotateY: 360, duration: 3, ease: "none", repeat: -1})

    faces.value.addEventListener("mouseenter", () => {
      anim.timeScale(10)
    })
    faces.value.addEventListener("mouseleave", () => {
      anim.timeScale(1)
    })
  })
</script>

<template>
  <div class="card">
    <div ref="faces" class="faces">
      <div class="face front"><img src="../assets/img/jm bourgeois.jpg" alt="jc"></div>
      <div class="face back"><img src="../assets/img/jesus christ.jpg" alt="jc"></div>
    </div>
  </div>
</template>

<style>
  .card{
    width: 15vw;
    height: 21vw;
    perspective: 1000px;
  }
  .faces{
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
  }
  .face{
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    position: absolute;
    backface-visibility: hidden;
    border-radius: 1vw;
    overflow: hidden;
    cursor: pointer;
  }
  .face > *{
    backface-visibility: hidden;
  }
  .face img{
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
  .face.front{
    background-color: salmon;
  }
  .face.back{
    background-color: cornflowerblue;
    transform: rotateY(180deg);
  }
</style>