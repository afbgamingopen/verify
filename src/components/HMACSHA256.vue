<script setup>
import { reactive, defineProps, watch } from "vue";
import hmacSHA256 from "crypto-js/hmac-sha256";
import Hex from "crypto-js/enc-hex";

const props = defineProps({
  secret: String,
  message: String,
  highLightCount: Number,
});
watch(props, () => {
  calc();
});
const calced = reactive({
  highLight: [],
  normal: [],
  digest: [],
  digestHex: "",
  digestBytes: [],
});
calc();

function calc() {
  calced.highLight.length = 0;
  calced.normal.length = 0;
  for (var i = 0; i < 32; i++) {
    if (i < props.highLightCount) {
      calced.highLight.push(i);
    } else {
      calced.normal.push(i);
    }
  }
  calced.digest = hmacSHA256(props.message, props.secret);
  calced.digestBytes = hmacDigestToBytes(calced.digest);
  calced.digestHex = Hex.stringify(calced.digest);
}

function hmacDigestToBytes(wordArray) {
  // Shortcuts
  var words = wordArray.words;
  var sigBytes = wordArray.sigBytes;

  // Convert
  var bytes = [];
  for (var i = 0; i < sigBytes; i++) {
    var bite = (words[i >>> 2] >>> (24 - (i % 4) * 8)) & 0xff;
    bytes.push(bite & 0xff);
  }

  return bytes;
}
</script>

<template>
  <div class="scrollX">
    <span class="highlight" style="font-family: monospace"
      >HMAC_SHA256({{ props.secret }},{{ props.message }})</span
    >
    <table>
      <tbody>
        <tr class="tr">
          <td class="td" v-for="n in calced.highLight" :key="n">
            <span class="highlight" style="font-family: monospace">{{
              calced.digestHex.substring(n * 2, n * 2 + 2)
            }}</span>
          </td>
          <td class="td" v-for="n in calced.normal" :key="n">
            <span style="font-family: monospace">{{
              calced.digestHex.substring(n * 2, n * 2 + 2)
            }}</span>
          </td>
        </tr>
        <tr class="tr">
          <td class="td" v-for="n in calced.highLight" :key="n">
            <span class="highlight" style="font-family: monospace">{{
              calced.digestBytes[n]
            }}</span>
          </td>
          <td class="td" v-for="n in calced.normal" :key="n">
            <span style="font-family: monospace">{{
              calced.digestBytes[n]
            }}</span>
          </td>
        </tr>
      </tbody>
    </table>
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
