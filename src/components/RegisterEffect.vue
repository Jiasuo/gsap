<script setup>
  import { onMounted, ref } from 'vue';
  import { gsap } from "gsap"
  import { GSDevTools } from 'gsap-trial/GSDevTools';
  import { SplitText } from "gsap-trial/SplitText"
  
  const wrapper = ref(null)
  
  gsap.registerPlugin(GSDevTools, SplitText)

  gsap.registerEffect({
    name: "staggerY",
    extendTimeline: true,
    defaults: {y: -100, stagger: 0.05, duration: 0.4, rotation: -100, ease: "back(3)"},
    effect: (targets, config) => {
      const {chars} = new SplitText(targets, {type: "chars"})
      const tl = gsap.timeline()
      tl.from(chars, {y: config.y, stagger: config.stagger, autoAlpha: 0, duration: config.duration, rotation: config.rotation, ease: config.ease})
      return tl
    }
  })
  
  
  onMounted(() => {
    gsap.set(wrapper.value, {autoAlpha: 1})
    const tl = gsap.timeline()
    tl.staggerY("h1").staggerY("h2", {y: 100, rotation: 100, ease: "elastic(5)", stagger: 0.01})
    GSDevTools.create({animation: tl})
  })
  </script>
  
  <template>
    <div ref="wrapper" class="wrapper">
      <h1>I'm a Fucking SQUi i i i i i i i i i i i i i i i D</h1>
      <h2>Io IO io Io IO io Io IO io Io IO io Io IO io Io IO</h2>
    </div>
  </template>
  
  <style scoped>
    .wrapper {
      perspective: 800px;
      height: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      visibility: hidden;
    }
    h2{
      margin-top: 50px;
    }
  </style>
  