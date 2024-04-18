<script setup>
import { defineProps } from "vue";
import Slider from "./dice-slider.vue";
import Slide from "./dice-slide.vue";
import Result from "./dice-result.vue";
import HMACSHA256 from "./HMACSHA256.vue";
import BytesToNumber from "./BytesToNumber.vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
const index03 = [0, 1, 2, 3];
const index4 = [
  4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24,
  25, 26, 27, 28, 29, 30, 31,
];
</script>

<template>
  <div class="result">
    <div class="row-wrap">
      <h2>Final Result</h2>
      <div class="scrollX">
        <span class="highlight" style="font-family: monospace">{{
          data.finalResult
        }}</span>
      </div>
    </div>
    <div class="row-wrap">
      <h2 style="">Casino Seeds to Bytes</h2>
      <HMACSHA256
        :secret="data.serverSeed"
        :message="data.clientSeed + ':' + data.nonce + ':' + data.cursor"
        :highLightCount="4"
      ></HMACSHA256>
    </div>
    <div class="row-wrap">
      <h2 style="">Bytes to Number</h2>
      <div class="wrap scrollX">
        <BytesToNumber
          :secret="data.serverSeed"
          :message="data.clientSeed + ':' + data.nonce + ':' + data.cursor"
          :byteIndex="0"
          :maxRange="10001"
        ></BytesToNumber>
      </div>
    </div>
  </div>
</template>

<style scoped>
.row-wrap {
  display: flex;
  flex-direction: column;
  max-width: 700px;
}

h2 {
  padding: 0.5em 0;
}

.highlight {
  color: white;
  font-weight: 500;
}
</style>
