<script setup>
import { defineProps } from "vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
</script>

<template>
  <div class="wrap svelte-wtusq6">
    <div class="wrap svelte-k21gra">
      <div class="hand-wrap svelte-k21gra" data-test="banker-hand">
        <div class="desc svelte-k21gra"><span>Player</span></div>
        <div
          :class="['wrap', data.playerWin, 'svelte-n07u8e']"
          style="
            --card-size-ratio: 1em;
            --slide-transition: 300ms;
            width: 7.5em;
            height: 8.9em;
            --min-height: 9.9em;
            --min-width: 10em;
          "
        >
          <div
            class="svelte-n07u8e dealt"
            data-test="card-1"
            style="
              margin-top: 0em;
              margin-left: 0em;
              animation-delay: 0ms;
              --muck-transition: 300ms;
              transition: transform 300ms ease 0s;
              transform: translate(0px, 0px);
            "
          >
            <div class="pokerBorder">
              <img class="poker" :src="data.playerPoker[0].image" />
            </div>
          </div>
          <div
            class="svelte-n07u8e dealt"
            data-test="card-2"
            style="
              margin-top: 1em;
              margin-left: -2.5em;
              animation-delay: 100ms;
              --muck-transition: 300ms;
              transition: transform 300ms ease 0s;
              transform: translate(0px, 0px);
            "
          >
            <div class="pokerBorder">
              <img class="poker" :src="data.playerPoker[1].image" />
            </div>
          </div>
          <div
            v-if="data.playerPoker.length > 2"
            class="svelte-n07u8e dealt"
            data-test="card-3"
            style="
              margin-top: 2em;
              margin-left: -2.5em;
              animation-delay: 200ms;
              --muck-transition: 300ms;
              transition: transform 300ms ease 0s;
              transform: translate(0px, 0px);
            "
          >
            <div>
              <div class="pokerBorder">
                <img class="poker" :src="data.playerPoker[2].image" />
              </div>
            </div>
          </div>
          <div :class="['value', data.playerWin, 'svelte-n07u8e']">
            {{ data.playerPoint }}
          </div>
        </div>
      </div>
      <div class="hand-wrap svelte-k21gra">
        <div class="desc svelte-k21gra"><span>Banker</span></div>
        <div
          :class="['wrap', data.bankerWin, 'svelte-n07u8e']"
          style="
            --card-size-ratio: 1em;
            --slide-transition: 300ms;
            width: 7.5em;
            height: 8.9em;
            --min-height: 9.9em;
            --min-width: 10em;
          "
        >
          <div
            class="svelte-n07u8e dealt"
            data-test="card-1"
            style="
              margin-top: 0em;
              margin-left: 0em;
              animation-delay: 0ms;
              --muck-transition: 300ms;
              transition: transform 300ms ease 0s;
              transform: translate(0px, 0px);
            "
          >
            <div class="pokerBorder">
              <img class="poker" :src="data.bankerPoker[0].image" />
            </div>
          </div>
          <div
            class="svelte-n07u8e dealt"
            data-test="card-2"
            style="
              margin-top: 1em;
              margin-left: -2.5em;
              animation-delay: 100ms;
              --muck-transition: 300ms;
              transition: transform 300ms ease 0s;
              transform: translate(0px, 0px);
            "
          >
            <div class="pokerBorder">
              <img class="poker" :src="data.bankerPoker[1].image" />
            </div>
          </div>
          <div
            v-if="data.bankerPoker.length > 2"
            class="svelte-n07u8e dealt"
            data-test="card-3"
            style="
              margin-top: 2em;
              margin-left: -2.5em;
              animation-delay: 100ms;
              --muck-transition: 300ms;
              transition: transform 300ms ease 0s;
              transform: translate(0px, 0px);
            "
          >
            <div class="pokerBorder">
              <img class="poker" :src="data.bankerPoker[2].image" />
            </div>
          </div>
          <div :class="['value', data.bankerWin, 'svelte-n07u8e']">
            {{ data.bankerPoint }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.wrap.svelte-1xr9o8z {
  width: 100%;
}

.wrap.svelte-1xr9o8z > label {
  width: 100%;
}

.wrap.svelte-wtusq6 {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  text-align: left;
  min-height: 200px;
  max-width: 700px;
  padding: var(--spacingEm-1);
  border: dotted 2px var(--grey-400);
  border-radius: var(--border-radius-0-5);
}

.wrap.svelte-wtusq6 > * + * {
  margin-top: var(--spacingEm-1);
}

.tile-wrap.svelte-k21gra {
  width: 100%;
  padding-top: var(--spacing-1);
}

.wrap.svelte-k21gra {
  flex: 1;
  width: 100%;
  grid-gap: var(--spacingEm-1);
  display: grid;
  overflow: hidden;
  grid-template-rows: repeat(2, -webkit-max-content);
  grid-template-rows: repeat(2, max-content);
  padding-bottom: var(--spacingEm-1);
}

.hand-wrap.svelte-k21gra {
  position: relative;
  width: 100%;
  display: grid;
  grid-gap: var(--spacingEm-1);
  align-content: space-between;
  justify-content: center;
}

.desc.svelte-k21gra {
  color: var(--label-color);
  font-size: var(--label-font-size);
  font-weight: var(--label-font-weight);
  letter-spacing: var(--label-letter-spacing);
  text-align: center;
}

.wrap.svelte-n07u8e {
  display: flex;
  position: relative;
  align-items: flex-start;
  margin-top: 1em;
  font-size: var(--card-size-ratio);
  min-width: var(--min-width);
  min-height: var(--min-height);
  transition-duration: var(--slide-transition);
}

@-webkit-keyframes svelte-n07u8e-muckCard {
  to {
    opacity: 0;
    transform: translate(-10%, 10%);
  }
}

@keyframes svelte-n07u8e-muckCard {
  to {
    opacity: 0;
    transform: translate(-10%, 10%);
  }
}

.content.dealt.svelte-n07u8e {
  opacity: 1;
}

.content.svelte-n07u8e:not(.dealt) {
  opacity: 0;
}

.content.mucked.svelte-n07u8e {
  -webkit-animation-name: svelte-n07u8e-muckCard;
  animation-name: svelte-n07u8e-muckCard;
  -webkit-animation-duration: var(--muck-transition);
  animation-duration: var(--muck-transition);
  -webkit-animation-fill-mode: forwards;
  animation-fill-mode: forwards;
}

.value.svelte-n07u8e {
  font-size: var(--text-size-default);
  position: absolute;
  top: 0;
  left: 100%;
  border-radius: 999px;
  padding: var(--spacing-0-25) var(--spacing-0-5);
  font-weight: 800;
  color: var(--white);
  width: 7ch;
  text-align: center;
  transform: translate(-100%, -100%);
  transition-duration: 0.3s;
  transition-property: background, color, transform, opacity;
  transition-timing-function: ease-out;
  box-shadow: var(--shadows-sm);
}

.value.hide.svelte-n07u8e {
  opacity: 0;
}

.value.active.svelte-n07u8e {
  background: var(--blue-400);
  color: var(--blue-800);
}

.value.win.svelte-n07u8e {
  background: var(--green-400);
  color: var(--green-800);
}

.value.draw.svelte-n07u8e {
  background: var(--yellow-500);
  color: var(--yellow-800);
}

.value.lose.svelte-n07u8e {
  background: var(--red-400);
  color: var(--red-800);
}

.value.none.svelte-n07u8e {
  background: var(--grey-400);
}

.back.svelte-1wtyksp {
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 0.25em;
  background: #fff;
  background-color: #fff;
  background-position: center;
  background-repeat: no-repeat;
  background-size: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

.face.svelte-1wtyksp {
  position: absolute;
  width: 100%;
  height: 100%;
  border-radius: 0.25em;
  background: #fff;
  transform: scaleX(-1);
}

.face.win.svelte-1wtyksp {
  box-shadow: 0 0 0 0.3em var(--green-500);
}

.face.lose.svelte-1wtyksp {
  box-shadow: 0 0 0 0.3em var(--red-400);
}

.face.draw.svelte-1wtyksp {
  box-shadow: 0 0 0 0.3em var(--yellow-500);
}

.face.active.svelte-1wtyksp {
  box-shadow: 0 0 0 0.3em var(--blue-500);
}

.horizontal.svelte-1wtyksp {
  transition: var(--transition-time);
  transition-timing-function: ease-out;
  transition-property: transform;
}

.horizontal.rotated.svelte-1wtyksp {
  transform: rotate(90deg);
}

.content.svelte-1wtyksp {
  position: relative;
  font-family: brandon-grotesque, sans-serif;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  perspective: 700px;
  transition: var(--transition-time);
  transform-style: preserve-3d;
  transition-timing-function: ease-out;
  transition-property: transform, box-shadow;
  box-shadow: 0 0 0.25em #0710174d;
  border-radius: 0.25em;
}

.content.svelte-1wtyksp:not(.face-down) {
  transform: rotateY(180deg);
}

.wrap.svelte-1wtyksp:disabled {
  pointer-events: none;
}

.face-content.svelte-soy9i6 {
  display: flex;
  flex-direction: column;
  align-items: center;
  font-size: 2.2em;
  width: -webkit-max-content;
  width: -moz-max-content;
  width: max-content;
  margin-left: 10%;
}

.wrap.svelte-n07u8e {
  display: flex;
  position: relative;
  align-items: flex-start;
  margin-top: 1em;
  font-size: var(--card-size-ratio);
  min-width: var(--min-width);
  min-height: var(--min-height);
  transition-duration: var(--slide-transition);
}

@-webkit-keyframes svelte-n07u8e-muckCard {
  to {
    opacity: 0;
    transform: translate(-10%, 10%);
  }
}

@keyframes svelte-n07u8e-muckCard {
  to {
    opacity: 0;
    transform: translate(-10%, 10%);
  }
}

.content.dealt.svelte-n07u8e {
  opacity: 1;
}

.content.svelte-n07u8e:not(.dealt) {
  opacity: 0;
}

.content.mucked.svelte-n07u8e {
  -webkit-animation-name: svelte-n07u8e-muckCard;
  animation-name: svelte-n07u8e-muckCard;
  -webkit-animation-duration: var(--muck-transition);
  animation-duration: var(--muck-transition);
  -webkit-animation-fill-mode: forwards;
  animation-fill-mode: forwards;
}

.value.svelte-n07u8e {
  font-size: var(--text-size-default);
  position: absolute;
  top: 0;
  left: 100%;
  border-radius: 999px;
  padding: var(--spacing-0-25) var(--spacing-0-5);
  font-weight: 800;
  color: var(--white);
  width: 7ch;
  text-align: center;
  transform: translate(-100%, -100%);
  transition-duration: 0.3s;
  transition-property: background, color, transform, opacity;
  transition-timing-function: ease-out;
  box-shadow: var(--shadows-sm);
}

.value.hide.svelte-n07u8e {
  opacity: 0;
}

.value.active.svelte-n07u8e {
  background: var(--blue-400);
  color: var(--blue-800);
}

.value.win.svelte-n07u8e {
  background: var(--green-400);
  color: var(--green-800);
}

.value.draw.svelte-n07u8e {
  background: var(--yellow-500);
  color: var(--yellow-800);
}

.value.lose.svelte-n07u8e {
  background: var(--red-400);
  color: var(--red-800);
}

.value.none.svelte-n07u8e {
  background: var(--grey-400);
}

.svg-icon.svelte-10mcogx {
  pointer-events: none;
  stroke-width: 0;
  stroke: currentColor;
  fill: currentColor;
  flex-shrink: 0;
  display: inline-block;
  width: 1em;
  height: 1em;
}

img.svelte-10mcogx {
  display: inline-block;
  width: 1em;
  height: 1em;
}

@-webkit-keyframes svelte-1icrd1j-roll {
  0%,
  5% {
    transform: rotate(0) translate(0);
  }

  15% {
    transform: rotate(45deg) translate(-10%, -10%);
  }

  20%,
  30% {
    transform: rotate(90deg) translate(0);
  }

  37.5% {
    transform: rotate(135deg) translate(-10%, 10%);
  }

  45%,
  55% {
    transform: rotate(180deg) translate(0);
  }

  62.5% {
    transform: rotate(225deg) translate(10%, 10%);
  }

  70%,
  80% {
    transform: rotate(270deg) translate(0);
  }

  87.5% {
    transform: rotate(315deg) translate(10%, -10%);
  }

  95%,
  to {
    transform: rotate(360deg) translate(0);
  }
}

@keyframes svelte-1icrd1j-roll {
  0%,
  5% {
    transform: rotate(0) translate(0);
  }

  15% {
    transform: rotate(45deg) translate(-10%, -10%);
  }

  20%,
  30% {
    transform: rotate(90deg) translate(0);
  }

  37.5% {
    transform: rotate(135deg) translate(-10%, 10%);
  }

  45%,
  55% {
    transform: rotate(180deg) translate(0);
  }

  62.5% {
    transform: rotate(225deg) translate(10%, 10%);
  }

  70%,
  80% {
    transform: rotate(270deg) translate(0);
  }

  87.5% {
    transform: rotate(315deg) translate(10%, -10%);
  }

  95%,
  to {
    transform: rotate(360deg) translate(0);
  }
}

.roll.svelte-1icrd1j {
  display: inline-flex;
  position: relative;
}

.roll.svelte-1icrd1j > .svg-icon {
  transform-origin: center;
  -webkit-animation-name: svelte-1icrd1j-roll;
  animation-name: svelte-1icrd1j-roll;
  -webkit-animation-duration: 1.6s;
  animation-duration: 1.6s;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
  -webkit-animation-timing-function: linear;
  animation-timing-function: linear;
}

@-webkit-keyframes svelte-1icrd1j-flipY {
  50% {
    transform: rotateY(180deg) scale(1.2);
  }

  to {
    transform: rotateY(360deg);
  }
}

@keyframes svelte-1icrd1j-flipY {
  50% {
    transform: rotateY(180deg) scale(1.2);
  }

  to {
    transform: rotateY(360deg);
  }
}

.flipY.svelte-1icrd1j {
  -webkit-animation-name: svelte-1icrd1j-flipY;
  animation-name: svelte-1icrd1j-flipY;
  -webkit-animation-duration: 1.6s;
  animation-duration: 1.6s;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
}

@-webkit-keyframes svelte-1icrd1j-flipX {
  50% {
    transform: rotateX(180deg);
  }

  to {
    transform: rotateX(360deg);
  }
}

@keyframes svelte-1icrd1j-flipX {
  50% {
    transform: rotateX(180deg);
  }

  to {
    transform: rotateX(360deg);
  }
}

.flipX.svelte-1icrd1j {
  -webkit-animation-name: svelte-1icrd1j-flipX;
  animation-name: svelte-1icrd1j-flipX;
  -webkit-animation-duration: 1.6s;
  animation-duration: 1.6s;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
}

@-webkit-keyframes svelte-1icrd1j-spin {
  to {
    transform: rotate(360deg);
  }
}

@keyframes svelte-1icrd1j-spin {
  to {
    transform: rotate(360deg);
  }
}

.spin.svelte-1icrd1j {
  -webkit-animation-name: svelte-1icrd1j-spin;
  animation-name: svelte-1icrd1j-spin;
  -webkit-animation-duration: 1.6s;
  animation-duration: 1.6s;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
}

@-webkit-keyframes svelte-1icrd1j-wobble {
  25% {
    transform: scale(1.3);
  }

  50% {
    transform: scale(1.3) rotate(-10deg);
  }

  75% {
    transform: scale(1.3) rotate(10deg);
  }
}

@keyframes svelte-1icrd1j-wobble {
  25% {
    transform: scale(1.3);
  }

  50% {
    transform: scale(1.3) rotate(-10deg);
  }

  75% {
    transform: scale(1.3) rotate(10deg);
  }
}

.wobble.svelte-1icrd1j {
  -webkit-animation-name: svelte-1icrd1j-wobble;
  animation-name: svelte-1icrd1j-wobble;
  -webkit-animation-duration: 1s;
  animation-duration: 1s;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
  -webkit-animation-timing-function: cubic-bezier(0.87, -0.41, 0.19, 1.44);
  animation-timing-function: cubic-bezier(0.87, -0.41, 0.19, 1.44);
}

@-webkit-keyframes svelte-1icrd1j-bounce {
  10% {
    transform: translateY(-90%);
  }

  30% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-60%);
  }

  70% {
    transform: translateY(0);
  }

  90% {
    transform: translateY(-30%);
  }
}

@keyframes svelte-1icrd1j-bounce {
  10% {
    transform: translateY(-90%);
  }

  30% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-60%);
  }

  70% {
    transform: translateY(0);
  }

  90% {
    transform: translateY(-30%);
  }
}

.bounce.svelte-1icrd1j {
  -webkit-animation-name: svelte-1icrd1j-bounce;
  animation-name: svelte-1icrd1j-bounce;
  -webkit-animation-duration: 1.1s;
  animation-duration: 1.1s;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
}

@-webkit-keyframes svelte-1icrd1j-tick {
  0%,
  to {
    transform: rotate(30deg);
  }

  50% {
    transform: rotate(-80deg);
  }

  75% {
    transform: rotate(50deg);
  }
}

@keyframes svelte-1icrd1j-tick {
  0%,
  to {
    transform: rotate(30deg);
  }

  50% {
    transform: rotate(-80deg);
  }

  75% {
    transform: rotate(50deg);
  }
}

.tick.svelte-1icrd1j {
  -webkit-animation-name: svelte-1icrd1j-tick;
  animation-name: svelte-1icrd1j-tick;
  -webkit-animation-duration: 1s;
  animation-duration: 1s;
  -webkit-animation-iteration-count: infinite;
  animation-iteration-count: infinite;
  transform-origin: 50% 25%;
  -webkit-animation-timing-function: ease-in-out;
  animation-timing-function: ease-in-out;
}

.content-or-loader.svelte-1uofbko {
  display: inline-flex;
  position: relative;
  align-items: center;
}

.content-or-loader.truncate.svelte-1uofbko > span:not(.svg-icon) {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  display: inherit;
  display: inline-block;
}

.content-or-loader.loading.svelte-1uofbko {
  visibility: hidden;
}

.content-or-loader.svelte-1uofbko > * + * {
  margin-left: var(--spacing-0-5);
}

.loader.svelte-1uofbko {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%) !important;
}

.loader.svelte-1uofbko > * {
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.wrap.svelte-n07u8e {
  display: flex;
  position: relative;
  align-items: flex-start;
  margin-top: 1em;
  font-size: var(--card-size-ratio);
  min-width: var(--min-width);
  min-height: var(--min-height);
  transition-duration: var(--slide-transition);
}

@-webkit-keyframes svelte-n07u8e-muckCard {
  to {
    opacity: 0;
    transform: translate(-10%, 10%);
  }
}

@keyframes svelte-n07u8e-muckCard {
  to {
    opacity: 0;
    transform: translate(-10%, 10%);
  }
}

.content.dealt.svelte-n07u8e {
  opacity: 1;
}

.content.svelte-n07u8e:not(.dealt) {
  opacity: 0;
}

.content.mucked.svelte-n07u8e {
  -webkit-animation-name: svelte-n07u8e-muckCard;
  animation-name: svelte-n07u8e-muckCard;
  -webkit-animation-duration: var(--muck-transition);
  animation-duration: var(--muck-transition);
  -webkit-animation-fill-mode: forwards;
  animation-fill-mode: forwards;
}

.value.svelte-n07u8e {
  font-size: var(--text-size-default);
  position: absolute;
  top: 0;
  left: 100%;
  border-radius: 999px;
  padding: var(--spacing-0-25) var(--spacing-0-5);
  font-weight: 800;
  color: var(--white);
  width: 7ch;
  text-align: center;
  transform: translate(-100%, -100%);
  transition-duration: 0.3s;
  transition-property: background, color, transform, opacity;
  transition-timing-function: ease-out;
  box-shadow: var(--shadows-sm);
}

.value.hide.svelte-n07u8e {
  opacity: 0;
}

.value.active.svelte-n07u8e {
  background: var(--blue-400);
  color: var(--blue-800);
}

.value.win.svelte-n07u8e {
  background: var(--green-400);
  color: var(--green-800);
}

.value.draw.svelte-n07u8e {
  background: var(--yellow-500);
  color: var(--yellow-800);
}

.value.lose.svelte-n07u8e {
  background: var(--red-400);
  color: var(--red-800);
}

.value.none.svelte-n07u8e {
  background: var(--grey-400);
}

.pokerBorder {
  border-radius: 0.5em;
  width: 6em;
  height: 8.3em;
}

.poker {
  width: 6em;
  border-radius: 0.25em;
}

.lose .pokerBorder {
  box-shadow: 0 0 0 0.1em var(--red-500);
}

.win .pokerBorder {
  box-shadow: 0 0 0 0.1em var(--green-500);
}

.none .pokerBorder {
  box-shadow: 0 0 0 0.1em var(--grey-500);
}

.lose .poker {
  box-shadow: inset 0 0 0 0.4em var(--red-500);
}

.win .poker {
  box-shadow: inset 0 0 0 0.4em var(--green-500);
}

.none .poker {
  box-shadow: inset 0 0 0 0.4em var(--grey-500);
}
</style>
