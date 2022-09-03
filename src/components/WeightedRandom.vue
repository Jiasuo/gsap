<script setup>
import {gsap} from "gsap"
import { onMounted } from "vue";

// reusable function. Feed in an array and an ease and it'll return 
// a function that pulls a random element from that array, weighted
// according to the ease you provide.
function weightedRandom(collection, ease) {
	return gsap.utils.pipe(
		Math.random,            //random number between 0 and 1
		gsap.parseEase(ease),   //apply the ease
		gsap.utils.mapRange(0, 1, -0.5, collection.length-0.5), //map to the index range of the array, stretched by 0.5 each direction because we'll round and want to keep distribution (otherwise linear distribution would be center-weighted slightly)
		gsap.utils.snap(1),     //snap to the closest integer
		i => collection[i]      //return that element from the array
	);
}

const colors = ["orange", "yellow", "blue"]

const intervals = [];

onMounted(() => {
  gsap.to(".box", {
    backgroundColor: weightedRandom(colors, "power1"),
    y: function(index, target, all){
      intervals.push(setInterval(() =>{
        console.log(`${index}:`, target.style.backgroundColor);
      }, 0.1))
      return index * 30
    },
    onComplete(){
      intervals.forEach((v, i) =>{
        clearInterval(v)
      })
    },
    stagger: {
      amount: 3,
      from: "center",
      ease: "linear"
    },
    duration: 2
  })
})
</script>

<template>
  <div class="wrapper">
    <div class="box">1</div>
    <div class="box">2</div>
    <div class="box">3</div>
    <div class="box">4</div>
    <div class="box">5</div>
    <div class="box">6</div>
    <div class="box">7</div>
    <div class="box">8</div>
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