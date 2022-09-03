<script setup>
  import { onMounted, ref } from 'vue';
  import { gsap } from "gsap"
  import { GSDevTools } from 'gsap-trial/GSDevTools';
  import { SplitText } from "gsap-trial/SplitText"
  
  const wrapper = ref(null)
  
  gsap.registerPlugin(GSDevTools, SplitText)
  
  
  onMounted(() => {
    gsap.set(wrapper.value, {autoAlpha: 1})
    const split = new SplitText("h1", {type: "chars"})
    const tl = gsap.timeline()
    tl.from(split.chars, {
      opacity: 0,
      y: gsap.utils.wrap([-100, 100]),
      rotation: gsap.utils.wrap([-100, 100]),
      ease: "Power1.out",
      stagger: 0.05})
    GSDevTools.create({animation: tl})
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
  