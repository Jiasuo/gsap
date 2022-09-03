<script setup>
import { gsap } from "gsap"
import { onMounted } from "vue";

function y(index, target, all) {
  const filtered = all.filter(t => !t.classList.contains("b"))
  const targetNewIndex = filtered.indexOf(target)
  if(target.classList.contains("b")){
    return 300;
  }
  return index * 20
}

onMounted(() => {
  gsap.set(".box", { autoAlpha: 0 })
  gsap.to(".box", {
    y,
    autoAlpha: 1,
    stagger: 0.05,
    ease: "Power3.inOut"
  })
})
</script>

<template>
  <div class="wrapper">
    <div class="box">1</div>
    <div class="box">2</div>
    <div class="box b">3</div>
    <div class="box">4</div>
    <div class="box">5</div>
    <div class="box b">6</div>
    <div class="box">7</div>
    <div class="box b">8</div>
    <div class="box">9</div>
    <div class="box">10</div>
  </div>
</template>

<style>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.box {
  width: 4vw;
  height: 4vw;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 0.86vw;
  background-color: blanchedalmond;
  color: #444;
}

.box:not(:first-child) {
  margin-left: 0.5vw;
}
</style>