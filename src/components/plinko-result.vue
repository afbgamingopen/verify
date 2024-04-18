<script setup>
import { defineProps } from "vue";
import HMACSHA256 from "./HMACSHA256.vue";
import BytesToNumber from "./BytesToNumber.vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
</script>

<template>
  <div class="result">
    <div class="row-wrap svelte-1j9612g">
      <h2
        class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
        style=""
      >
        Final Result
      </h2>
      <div class="scrollX plinko-result">
        <div class="wrap svelte-1lfzokq">
          <span
            class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-4ickvp"
            style="font-family: monospace"
            >Payout index: {{ data.plinkoPayoutIndex }} =
            {{ data.result }}</span
          >
          <table>
            <tbody>
              <tr class="tr svelte-1lfzokq">
                <td
                  v-for="(n, index) in data.plinkoRows"
                  :key="index"
                  :class="[index == data.result && 'active']"
                  class="td svelte-1lfzokq"
                >
                  <span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-4ickvp"
                    style="font-family: monospace"
                    >{{ n }}</span
                  >
                </td>
              </tr>
              <tr class="tr svelte-1lfzokq">
                <td
                  v-for="(n, index) in data.plinkoPayout"
                  :key="index"
                  :class="[index == data.result && 'active']"
                  class="td svelte-1lfzokq"
                >
                  <span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-4ickvp"
                    style="font-family: monospace"
                    >{{ n }}</span
                  >
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
    <div class="row-wrap svelte-1j9612g">
      <h2
        class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
        style=""
      >
        Casino Seeds to Bytes
      </h2>
      <HMACSHA256
        :secret="data.serverSeed"
        :message="data.clientSeed + ':' + data.nonce + ':0'"
        :highLightCount="32"
      ></HMACSHA256>
      <HMACSHA256
        :secret="data.serverSeed"
        :message="data.clientSeed + ':' + data.nonce + ':1'"
        :highLightCount="32"
      ></HMACSHA256>
      <HMACSHA256
        :secret="data.serverSeed"
        :message="data.clientSeed + ':' + data.nonce + ':2'"
        :highLightCount="16"
      ></HMACSHA256>
    </div>
    <div class="row-wrap svelte-1j9612g">
      <h2
        class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
        style=""
      >
        Bytes to Number
      </h2>
      <div class="wrap scrollX" style="display: flex; flex-direction: row">
        <template v-for="idx in [0, 4, 8, 12, 16, 20, 24, 28]" :key="idx">
          <BytesToNumber
            :secret="data.serverSeed"
            :message="data.clientSeed + ':' + data.nonce + ':0'"
            :byteIndex="idx"
            :maxRange="2"
          ></BytesToNumber>
        </template>
        <template v-for="idx in [0, 4, 8, 12, 16, 20, 24, 28]" :key="idx">
          <BytesToNumber
            :secret="data.serverSeed"
            :message="data.clientSeed + ':' + data.nonce + ':1'"
            :byteIndex="idx"
            :maxRange="2"
          ></BytesToNumber>
        </template>
        <template v-for="idx in [0, 4, 8, 12]" :key="idx">
          <BytesToNumber
            :secret="data.serverSeed"
            :message="data.clientSeed + ':' + data.nonce + ':2'"
            :byteIndex="idx"
            :maxRange="2"
          ></BytesToNumber>
        </template>
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
  color: white !important;
  font-weight: 500;
}

.column {
  display: flex;
  width: -webkit-fit-content;
  width: -moz-fit-content;
  width: fit-content;
  flex-direction: column;
}

.scrollX div:not(:first-child) {
  margin-left: 4rem;
}

.result .plinko-result .active span {
  color: rgb(255, 137, 18);
}
</style>
