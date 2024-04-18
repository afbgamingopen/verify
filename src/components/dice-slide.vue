<script setup>
import Num from "./dice-num.vue";
</script>

<template>
  <div
    class="wrap svelte-1hc4rro"
    data-test-dice-condition="above"
    style="--slider-height: 8px; --max-game-board-width: 730px"
  >
    <Num class="svelte-16rlbb1" />
    <div class="slidecontent svelte-1hc4rro">
      <div class="range svelte-1hc4rro">
        <div class="lower above svelte-1hc4rro"></div>
        <div class="higher above svelte-1hc4rro" style="width: 0%"></div>
      </div>
      <input
        disabled=""
        min="2"
        max="98"
        type="range"
        class="classic-slider svelte-1hc4rro"
        data-test="dice-slider"
      />
    </div>
  </div>
</template>

<style scoped>
.classic-slider.svelte-1hc4rro {
  -webkit-appearance: none;
  width: 100%;
  position: absolute;
  z-index: 10;
  background: transparent;
  top: 0;
  height: var(--slider-height);
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro:focus {
  outline: none;
}

.classic-slider.svelte-1hc4rro::-webkit-slider-runnable-track {
  width: 100%;
  height: var(--slider-height);
  cursor: pointer;
  background: transparent;
  border: none;
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro::-moz-range-track {
  width: 100%;
  height: var(--slider-height);
  cursor: pointer;
  background: transparent;
  border: none;
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro::-ms-track {
  width: 100%;
  height: var(--slider-height);
  cursor: pointer;
  background: transparent;
  border: none;
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro::-webkit-slider-thumb {
  margin-top: calc(var(--slider-height) * -1);
  height: var(--drag-size);
  width: var(--drag-size);
  border: none;
  background-color: var(--blue-400);
  background-image: var(--lines-asset);
  background-position: center;
  background-repeat: no-repeat;
  background-size: 40%;
  cursor: -webkit-grab;
  cursor: grab;
  -webkit-appearance: none;
  border-radius: var(--border-radius-0-25);
  box-shadow: var(--shadows-md);
  transform: translateY(calc(var(--slider-height) * -1));
  pointer-events: auto;
}

.classic-slider.svelte-1hc4rro::-webkit-slider-thumb:active {
  cursor: -webkit-grabbing;
  cursor: grabbing;
}

.classic-slider.svelte-1hc4rro::-moz-range-thumb {
  height: var(--drag-size);
  width: var(--drag-size);
  border: none;
  background-color: var(--blue-400);
  background-image: var(--lines-asset);
  background-position: center;
  background-repeat: no-repeat;
  background-size: 40%;
  cursor: grab;
  -webkit-appearance: none;
  border-radius: var(--border-radius-0-25);
  box-shadow: var(--shadows-md);
  transform: translateY(calc(var(--slider-height) * -1));
  pointer-events: auto;
}

.classic-slider.svelte-1hc4rro::-moz-range-thumb:active {
  cursor: grabbing;
}

.classic-slider.svelte-1hc4rro::-ms-thumb {
  height: var(--drag-size);
  width: var(--drag-size);
  border: none;
  background-color: var(--blue-400);
  background-image: var(--lines-asset);
  background-position: center;
  background-repeat: no-repeat;
  background-size: 40%;
  cursor: grab;
  -webkit-appearance: none;
  border-radius: var(--border-radius-0-25);
  box-shadow: var(--shadows-md);
  transform: translateY(calc(var(--slider-height) * -1));
  pointer-events: auto;
}

.classic-slider.svelte-1hc4rro::-ms-thumb:active {
  cursor: grabbing;
}

.classic-slider.svelte-1hc4rro::-ms-fill-lower {
  width: 100%;
  height: var(--slider-height);
  cursor: pointer;
  background: transparent;
  border: none;
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro::-ms-fill-upper {
  width: 100%;
  height: var(--slider-height);
  cursor: pointer;
  background: transparent;
  border: none;
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro:focus::-webkit-slider-runnable-track {
  width: 100%;
  height: var(--slider-height);
  cursor: pointer;
  background: transparent;
  border: none;
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro:focus::-ms-fill-lower {
  width: 100%;
  height: var(--slider-height);
  cursor: pointer;
  background: transparent;
  border: none;
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro:focus::-ms-fill-upper {
  width: 100%;
  height: var(--slider-height);
  cursor: pointer;
  background: transparent;
  border: none;
  pointer-events: none;
}

.classic-slider.svelte-1hc4rro:disabled::-webkit-slider-runnable-track {
  cursor: not-allowed;
}

.classic-slider.svelte-1hc4rro:disabled::-moz-range-track {
  cursor: not-allowed;
}

.classic-slider.svelte-1hc4rro:disabled::-ms-track {
  cursor: not-allowed;
}

.classic-slider.svelte-1hc4rro:disabled::-webkit-slider-thumb {
  cursor: not-allowed;
}

.classic-slider.svelte-1hc4rro:disabled::-moz-range-thumb {
  cursor: not-allowed;
}

.classic-slider.svelte-1hc4rro:disabled::-ms-thumb {
  cursor: not-allowed;
}

.classic-slider.svelte-1hc4rro:disabled::-ms-fill-lower {
  cursor: not-allowed;
}

.classic-slider.svelte-1hc4rro:disabled::-ms-fill-upper {
  cursor: not-allowed;
}

.wrap.svelte-1hc4rro {
  position: relative;
  width: 100%;
  max-width: var(--max-game-board-width);
  border-radius: 100px;
  padding: var(--spacingEm-1-5);
  background: var(--grey-400);
  text-align: left;
  margin: 4em 0;
  box-shadow: var(--shadows-md);
}

.slidecontent.svelte-1hc4rro {
  position: relative;
  height: var(--slider-height);
}

.range.svelte-1hc4rro {
  pointer-events: none;
  height: var(--slider-height);
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  border-radius: 100px;
  box-shadow: 0 0 0 10px var(--grey-700);
  transition: opacity 0.3s;
  overflow: hidden;
}

.lower.svelte-1hc4rro {
  position: absolute;
  height: var(--slider-height);
  width: 100%;
  right: 0;
  top: 0;
  border-radius: 100px;
}

.lower.above.svelte-1hc4rro {
  background: var(--green-500);
}

.lower.below.svelte-1hc4rro {
  background: var(--red-500);
}

.higher.svelte-1hc4rro {
  position: absolute;
  height: var(--slider-height);
  top: 0;
  left: 0;
  border-radius: 100px;
}

.higher.above.svelte-1hc4rro {
  background: var(--red-500);
}

.higher.below.svelte-1hc4rro {
  background: var(--green-500);
}
</style>
