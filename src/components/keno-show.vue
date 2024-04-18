<script setup>
import { defineProps } from "vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
const numbers = [
  0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21,
  22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39,
];
</script>

<template>
  <div class="wrap svelte-wtusq6">
    <div class="wrap svelte-7x447t">
      <div class="kenoShow">
        <div
          class="item"
          style="left: 22.5%; top: 0%"
          :class="[data.kenoFinalResult.indexOf(1) >= 0 && 'active']"
        >
          <img /><span>1</span>
        </div>
        <div
          class="item"
          style="left: 37.5%; top: 0%"
          :class="[data.kenoFinalResult.indexOf(2) >= 0 && 'active']"
        >
          <img /><span>2</span>
        </div>
        <div
          class="item"
          style="left: 52.5%; top: 0%"
          :class="[data.kenoFinalResult.indexOf(3) >= 0 && 'active']"
        >
          <img /><span>3</span>
        </div>
        <div
          class="item"
          style="left: 67.5%; top: 0%"
          :class="[data.kenoFinalResult.indexOf(4) >= 0 && 'active']"
        >
          <img /><span>4</span>
        </div>
        <div
          class="item"
          style="left: 0%; top: 15%"
          :class="[data.kenoFinalResult.indexOf(5) >= 0 && 'active']"
        >
          <img /><span>5</span>
        </div>
        <div
          class="item"
          style="left: 15%; top: 15%"
          :class="[data.kenoFinalResult.indexOf(6) >= 0 && 'active']"
        >
          <img /><span>6</span>
        </div>
        <div
          class="item"
          style="left: 30%; top: 15%"
          :class="[data.kenoFinalResult.indexOf(7) >= 0 && 'active']"
        >
          <img /><span>7</span>
        </div>
        <div
          class="item"
          style="left: 45%; top: 15%"
          :class="[data.kenoFinalResult.indexOf(8) >= 0 && 'active']"
        >
          <img /><span>8</span>
        </div>
        <div
          class="item"
          style="left: 60%; top: 15%"
          :class="[data.kenoFinalResult.indexOf(9) >= 0 && 'active']"
        >
          <img /><span>9</span>
        </div>
        <div
          class="item"
          style="left: 75%; top: 15%"
          :class="[data.kenoFinalResult.indexOf(10) >= 0 && 'active']"
        >
          <img /><span>10</span>
        </div>
        <div
          class="item"
          style="left: 90%; top: 15%"
          :class="[data.kenoFinalResult.indexOf(11) >= 0 && 'active']"
        >
          <img /><span>11</span>
        </div>
        <div
          class="item"
          style="left: 7.5%; top: 30%"
          :class="[data.kenoFinalResult.indexOf(12) >= 0 && 'active']"
        >
          <img /><span>12</span>
        </div>
        <div
          class="item"
          style="left: 22.5%; top: 30%"
          :class="[data.kenoFinalResult.indexOf(13) >= 0 && 'active']"
        >
          <img /><span>13</span>
        </div>
        <div
          class="item"
          style="left: 37.5%; top: 30%"
          :class="[data.kenoFinalResult.indexOf(14) >= 0 && 'active']"
        >
          <img /><span>14</span>
        </div>
        <div
          class="item"
          style="left: 52.5%; top: 30%"
          :class="[data.kenoFinalResult.indexOf(15) >= 0 && 'active']"
        >
          <img /><span>15</span>
        </div>
        <div
          class="item"
          style="left: 67.5%; top: 30%"
          :class="[data.kenoFinalResult.indexOf(16) >= 0 && 'active']"
        >
          <img /><span>16</span>
        </div>
        <div
          class="item"
          style="left: 83.5%; top: 30%"
          :class="[data.kenoFinalResult.indexOf(17) >= 0 && 'active']"
        >
          <img /><span>17</span>
        </div>
        <div
          class="item"
          style="left: 0%; top: 45%"
          :class="[data.kenoFinalResult.indexOf(18) >= 0 && 'active']"
        >
          <img /><span>18</span>
        </div>
        <div
          class="item"
          style="left: 15%; top: 45%"
          :class="[data.kenoFinalResult.indexOf(19) >= 0 && 'active']"
        >
          <img /><span>19</span>
        </div>
        <div
          class="item"
          style="left: 30%; top: 45%"
          :class="[data.kenoFinalResult.indexOf(20) >= 0 && 'active']"
        >
          <img /><span>20</span>
        </div>
        <div
          class="item"
          style="left: 60%; top: 45%"
          :class="[data.kenoFinalResult.indexOf(21) >= 0 && 'active']"
        >
          <img /><span>21</span>
        </div>
        <div
          class="item"
          style="left: 75%; top: 45%"
          :class="[data.kenoFinalResult.indexOf(22) >= 0 && 'active']"
        >
          <img /><span>22</span>
        </div>
        <div
          class="item"
          style="left: 90%; top: 45%"
          :class="[data.kenoFinalResult.indexOf(23) >= 0 && 'active']"
        >
          <img /><span>23</span>
        </div>
        <div
          class="item"
          style="left: 7.5%; top: 60%"
          :class="[data.kenoFinalResult.indexOf(24) >= 0 && 'active']"
        >
          <img /><span>24</span>
        </div>
        <div
          class="item"
          style="left: 22.5%; top: 60%"
          :class="[data.kenoFinalResult.indexOf(25) >= 0 && 'active']"
        >
          <img /><span>25</span>
        </div>
        <div
          class="item"
          style="left: 37.5%; top: 60%"
          :class="[data.kenoFinalResult.indexOf(26) >= 0 && 'active']"
        >
          <img /><span>26</span>
        </div>
        <div
          class="item"
          style="left: 52.5%; top: 60%"
          :class="[data.kenoFinalResult.indexOf(27) >= 0 && 'active']"
        >
          <img /><span>27</span>
        </div>
        <div
          class="item"
          style="left: 67.5%; top: 60%"
          :class="[data.kenoFinalResult.indexOf(28) >= 0 && 'active']"
        >
          <img /><span>28</span>
        </div>
        <div
          class="item"
          style="left: 83.5%; top: 60%"
          :class="[data.kenoFinalResult.indexOf(29) >= 0 && 'active']"
        >
          <img /><span>29</span>
        </div>
        <div
          class="item"
          style="left: 0%; top: 75%"
          :class="[data.kenoFinalResult.indexOf(30) >= 0 && 'active']"
        >
          <img /><span>30</span>
        </div>
        <div
          class="item"
          style="left: 15%; top: 75%"
          :class="[data.kenoFinalResult.indexOf(31) >= 0 && 'active']"
        >
          <img /><span>31</span>
        </div>
        <div
          class="item"
          style="left: 30%; top: 75%"
          :class="[data.kenoFinalResult.indexOf(32) >= 0 && 'active']"
        >
          <img /><span>32</span>
        </div>
        <div
          class="item"
          style="left: 45%; top: 75%"
          :class="[data.kenoFinalResult.indexOf(33) >= 0 && 'active']"
        >
          <img /><span>33</span>
        </div>
        <div
          class="item"
          style="left: 60%; top: 75%"
          :class="[data.kenoFinalResult.indexOf(34) >= 0 && 'active']"
        >
          <img /><span>34</span>
        </div>
        <div
          class="item"
          style="left: 75%; top: 75%"
          :class="[data.kenoFinalResult.indexOf(35) >= 0 && 'active']"
        >
          <img /><span>35</span>
        </div>
        <div
          class="item"
          style="left: 90%; top: 75%"
          :class="[data.kenoFinalResult.indexOf(36) >= 0 && 'active']"
        >
          <img /><span>36</span>
        </div>
        <div
          class="item"
          style="left: 22.5%; top: 90%"
          :class="[data.kenoFinalResult.indexOf(37) >= 0 && 'active']"
        >
          <img /><span>37</span>
        </div>
        <div
          class="item"
          style="left: 37.5%; top: 90%"
          :class="[data.kenoFinalResult.indexOf(38) >= 0 && 'active']"
        >
          <img /><span>38</span>
        </div>
        <div
          class="item"
          style="left: 52.5%; top: 90%"
          :class="[data.kenoFinalResult.indexOf(39) >= 0 && 'active']"
        >
          <img /><span>39</span>
        </div>
        <div
          class="item"
          style="left: 67.5%; top: 90%"
          :class="[data.kenoFinalResult.indexOf(40) >= 0 && 'active']"
        >
          <img /><span>40</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.kenoShow {
  width: 90%;
  height: 90%;
  padding-bottom: 80%;
  margin: 5% 5%;
}
.kenoShow .item {
  position: absolute;
  width: calc(12.5%);
  padding-bottom: 15.5%;
  transform: translate(-12.5%, -12.5%);
  font-size: 1.5em;
  font-weight: bold;
}

.kenoShow .item img {
  position: absolute;
  top: 0;
  left: 0;
  content: url("@/assets/keno.png");
  width: 100%;
}

.kenoShow .item span {
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100%;
  height: 100%;
  display: flex;
  align-items: center;
  align-content: center;
  justify-content: center;
  transform: translate(-50%, -50%);
}

.kenoShow .item.active {
  width: calc(12.5%);
  color: gold;
}
.kenoShow .item.active img {
  content: url("@/assets/keno-active.png");
}

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

.wrap.svelte-7x447t {
  width: 100%;
}

.tiles-wrap.svelte-7x447t {
  position: relative;
  display: grid;
  grid-gap: var(--spacingEm-1);
  grid-template-columns: repeat(8, auto);
  width: 100%;
  max-width: 700px;
}

@keyframes svelte-1f08dh7-reveal {
  0% {
    transform: translate(-50%, -50%) scale(0) rotate(-45deg);
  }

  to {
    transform: translate(-50%, -50%) scale(1) rotate(0);
  }
}

.gem.svelte-1f08dh7 {
  display: flex;
  position: absolute;
  top: 50%;
  left: 50%;
  width: 90%;
  transform: translate(-50%, -50%);
  animation-name: svelte-1f08dh7-reveal;
  animation-duration: var(--duration);
  animation-fill-mode: forwards;
  animation-timing-function: cubic-bezier(0.87, -0.41, 0.19, 1.44);
}

@keyframes svelte-e8x3gt-reveal {
  0% {
    opacity: 1;
  }

  to {
    transform: scale(0);
    opacity: 0;
  }
}

@keyframes svelte-e8x3gt-hide {
  0% {
    opacity: 0;
    transform: scale(0);
  }
}

.tile.svelte-e8x3gt.svelte-e8x3gt {
  position: relative;
  font-size: var(--spacingEm-1-5);
  font-weight: 600;
  color: var(--white);
  text-shadow: 0 3px 2px rgba(0, 0, 0, 0.1);
  border-radius: var(--border-radius-0-5);
  transition-duration: var(--duration);
  transition-property: background-color, box-shadow, opacity;
}

.tile.svelte-e8x3gt.svelte-e8x3gt:after {
  content: "";
  display: block;
  padding-bottom: 100%;
}

.tile.svelte-e8x3gt.svelte-e8x3gt:disabled,
.tile[disabled].svelte-e8x3gt.svelte-e8x3gt {
  opacity: 0.5;
  cursor: not-allowed;
  pointer-events: none;
}

.tile.revealed.svelte-e8x3gt.svelte-e8x3gt {
  background-color: var(--grey-900);
  box-shadow: inset 0 var(--shadow) #001017;
  color: var(--red-500);
}

.tile.match.svelte-e8x3gt.svelte-e8x3gt {
  background-color: var(--grey-900);
  box-shadow: 0 var(--shadow) var(--purple-600),
    0 0 0 0.3em var(--purple-400) inset;
  color: var(--green-700);
  text-shadow: 0 1px 1px var(--white);
}

.tile.match.svelte-e8x3gt.svelte-e8x3gt:disabled,
.tile.match[disabled].svelte-e8x3gt.svelte-e8x3gt {
  opacity: 1;
}

.tile.selected.svelte-e8x3gt.svelte-e8x3gt:disabled,
.tile.selected[disabled].svelte-e8x3gt.svelte-e8x3gt {
  opacity: 1;
}

.tile.svelte-e8x3gt .tile-number.svelte-e8x3gt {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  pointer-events: none;
}

.tile.svelte-e8x3gt .cover.svelte-e8x3gt {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  animation-fill-mode: forwards;
  border-radius: var(--border-radius-0-5);
  transition-duration: var(--duration);
  transition-property: background-color, box-shadow, transform;
}

.tile.svelte-e8x3gt .cover.hidden.svelte-e8x3gt {
  background: var(--grey-400);
  box-shadow: 0 var(--shadow) var(--grey-500);
  animation-name: svelte-e8x3gt-hide;
  animation-duration: var(--duration);
  animation-timing-function: cubic-bezier(0.87, -0.41, 0.19, 1.44);
}

.tile.svelte-e8x3gt .cover.hidden.svelte-e8x3gt:hover {
  background: var(--grey-300);
  box-shadow: 0 var(--tile-shadow-lg) var(--grey-400);
  transform: translateY(var(--tile-shadow-inset));
}

.tile.svelte-e8x3gt .cover.selected.svelte-e8x3gt {
  background-color: var(--purple-400);
  box-shadow: 0 var(--shadow) var(--purple-600);
  animation-name: svelte-e8x3gt-hide;
  animation-duration: var(--duration);
  animation-timing-function: cubic-bezier(0.87, -0.41, 0.19, 1.44);
}

.tile.svelte-e8x3gt .cover.selected.svelte-e8x3gt:hover {
  background-color: var(--purple-300);
  box-shadow: 0 var(--tile-shadow-lg) var(--purple-500);
  transform: translateY(var(--tile-shadow-inset));
}

.tile.svelte-e8x3gt .cover.revealed.svelte-e8x3gt {
  background: var(--green-400);
  box-shadow: 0 var(--shadow) var(--grey-500);
  opacity: 0;
  animation-name: svelte-e8x3gt-reveal;
  animation-duration: var(--duration);
}

.tile.svelte-e8x3gt .cover.match.svelte-e8x3gt {
  background-color: var(--purple-400);
  box-shadow: 0 var(--shadow) var(--purple-600);
  opacity: 0;
  animation-name: svelte-e8x3gt-reveal;
  animation-duration: var(--duration);
}

@keyframes svelte-1f08dh7-reveal {
  0% {
    transform: translate(-50%, -50%) scale(0) rotate(-45deg);
  }

  to {
    transform: translate(-50%, -50%) scale(1) rotate(0);
  }
}

.gem.svelte-1f08dh7 {
  display: flex;
  position: absolute;
  top: 50%;
  left: 55%;
  width: 90%;
  height: 90%;
  transform: translate(-50%, -50%);
  animation-name: svelte-1f08dh7-reveal;
  animation-duration: var(--duration);
  animation-fill-mode: forwards;
  animation-timing-function: cubic-bezier(0.87, -0.41, 0.19, 1.44);
}
</style>
