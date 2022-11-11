<script setup>
import { defineProps } from 'vue'
import Slider from './dice-slider.vue'
import Slide from './dice-slide.vue'
import Result from './dice-result.vue'
const props = defineProps({data:{type: Object}});
const data = props.data;
</script>

<template>
  <div class="translate-x svelte-hx4uck" v-bind:style="{'--dice-slide-transition':'300ms','transform': 'translate('+data.finalResult+'%, 0px)'}">
    <div class="hide-show positive svelte-hx4uck" style="--dice-scale-transition:500ms;"><img
        class="dice svelte-hx4uck" src="~@/assets/classic-dice.svg" alt="Dice">
      <div class="result positive svelte-hx4uck" style="--dice-result-transition:100ms;">{{data.finalResult}}</div>
    </div>
  </div>
</template>

<style scoped>

.translate-x.svelte-hx4uck {
  position: absolute;
  display: flex;
  bottom: 50%;
  left: 0;
  right: 0;
  z-index: 5;
  pointer-events: none;
  transition: transform var(--dice-slide-transition);
  will-change: transform
}

@-webkit-keyframes svelte-hx4uck-expand {
  50% {
      transform: scale(1.1) translate(-50%)
  }
}

@keyframes svelte-hx4uck-expand {
  50% {
      transform: scale(1.1) translate(-50%)
  }
}

.hide-show.svelte-hx4uck {
  position: relative;
  transform: translate(-50%);
  transition: all var(--dice-scale-transition);
  transform-origin: center bottom
}

.hide-show.positive.svelte-hx4uck,.hide-show.negative.svelte-hx4uck {
  -webkit-animation: svelte-hx4uck-expand var(--dice-scale-transition);
  animation: svelte-hx4uck-expand var(--dice-scale-transition)
}

.hide-show.is-hidden.svelte-hx4uck {
  transform: translate(-50%) scale(.8);
  opacity: 0
}

.result.svelte-hx4uck {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  text-shadow: 0 1px 0 #fff;
  font-weight: 600;
  transition: var(--dice-result-transition)
}

.result.positive.svelte-hx4uck {
  color: var(--green-600)
}

.result.negative.svelte-hx4uck {
  color: var(--red-500)
}

.result.neutral.svelte-hx4uck {
  color: var(--grey-200)
}

.dice.svelte-hx4uck {
  width: 7ch;
  height: auto;
  filter: drop-shadow(0 0 3px rgba(25,25,25,.1))
}

</style>
