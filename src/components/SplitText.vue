<script setup>
  import { onMounted, ref } from 'vue';
  import { gsap } from "gsap"
  import { SplitText } from "gsap-trial/SplitText"
  
  const wrapper = ref(null)
  
  gsap.registerPlugin(SplitText)
  
  
  onMounted(() => {
    gsap.set(wrapper.value, {autoAlpha: 1})
    const split = new SplitText("h1", {type: "chars"})
    gsap.timeline().from(split.chars, {opacity: 0, y: 50, ease: "back", stagger: 0.05, duration: 0.5})
  })
  </script>
  
  <template>
    <div ref="wrapper" class="wrapper">
      <h1>Letter by letter animation with GSAP</h1>
    </div>
  </template>
  
  <style scoped>
    .wrapper {
      perspective: 800px;
      height: 100%;
      display: flex;
      align-items: center;
      visibility: hidden;
    }
  </style>
  