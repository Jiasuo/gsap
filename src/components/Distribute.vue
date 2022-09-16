<script setup>
  import { onMounted, ref } from 'vue';
  import { gsap } from "gsap"
  import { SplitText } from "gsap-trial/SplitText"
  gsap.registerPlugin(SplitText)

  const h1 = ref(null)

  onMounted(() => {
    const {chars} = new SplitText(h1.value, {type: "chars"})
    console.log('chars', chars);
    gsap.from(chars, {
      scale: gsap.utils.distribute({
        base: 0.2,
        amount: 1.25, 
        from: "center",
        ease: "power1"
      }),
      x: gsap.utils.distribute({
        base: "-10vw",
        amount: "20vw",
        ease: "none"
      }),
      opacity: 0,
      repeat: -1,
      yoyo: true,
      stagger: {
        each: 0.01,
        from: "center",
      }
    })
  })
</script>

<template>
  <h1 ref="h1">HELLOOOOOOOOO</h1>
</template>

<style scoped>
  h1{
    font-family: "Kanit";
    font-size: 5vw;
  }
</style>