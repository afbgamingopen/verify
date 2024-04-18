<script setup>
import { defineProps } from 'vue'
import HMACSHA256 from './HMACSHA256.vue'
import BytesToNumber from './BytesToNumber.vue'
const props = defineProps({ data: { type: Object } });
const data = props.data;
</script>

<template>
    <div class="result">
        <div class="row-wrap svelte-1j9612g">
            <h2 class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
                style="">Final Result</h2>
            <div class="scrollX kenoResult">
                <p class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-1myjzud"
                    style="font-family: monospace;">({{ data.kenoCalcResult.join(", ") }})</p>
                <p class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-1myjzud"
                    style="font-family: monospace;">+ 1 =</p> <span
                    class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-1myjzud"
                    style="font-family: monospace;">({{ data.kenoFinalResult.join(", ") }})</span>
            </div>
        </div>
        <div class="row-wrap svelte-1j9612g">
            <h2 class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
                style="">Casino Seeds to Bytes</h2>
            <HMACSHA256 :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :highLightCount="32">
            </HMACSHA256>
            <HMACSHA256 :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':1'" :highLightCount="8">
            </HMACSHA256>
        </div>
        <div class="row-wrap svelte-1j9612g">
            <h2 class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
                style="">Bytes to Number</h2>
            <div class="wrap scrollX" style="display: flex;flex-direction: row;">
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :byteIndex="0"
                    :maxRange="40"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :byteIndex="4"
                    :maxRange="39"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :byteIndex="8"
                    :maxRange="38"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :byteIndex="12"
                    :maxRange="37"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :byteIndex="16"
                    :maxRange="36"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :byteIndex="20"
                    :maxRange="35"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :byteIndex="24"
                    :maxRange="34"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':0'" :byteIndex="28"
                    :maxRange="33"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':1'" :byteIndex="0"
                    :maxRange="32"></BytesToNumber>
                <BytesToNumber :secret="data.serverSeed" :message="data.clientSeed + ':' + data.nonce + ':1'" :byteIndex="4"
                    :maxRange="31"></BytesToNumber>
            </div>
        </div>
        <div class="row-wrap svelte-1j9612g">
            <h2 class="weight-semibold line-height-default align-left size-default text-size-default variant-subtle with-icon-space svelte-4ickvp"
                style="">Number to Shuffle</h2>
            <div class="wrap scrollX" style="display: flex;flex-direction: row;">
                <table>
                    <tbody>
                        <tr v-for="(nums, rowIndex) in data.kenoNumberToShuffle" :key="rowIndex" class="tr svelte-1lfzokq">
                            <td v-for="(num, colIndex) in nums" :key="colIndex" class="td svelte-1lfzokq">
                                <span class="weight-semibold line-height-default align-left size-medium text-size-medium variant-highlighted with-icon-space svelte-4ickvp"
                                    :class="[num==data.kenoCalcResult[rowIndex] && 'active']"
                                    style="font-family: monospace;">{{num}}</span> </td>
                        </tr>
                    </tbody>
                </table>
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

em.variant-highlighted.svelte-1myjzud,span.variant-highlighted.svelte-1myjzud,h1.variant-highlighted.svelte-1myjzud,h2.variant-highlighted.svelte-1myjzud,h3.variant-highlighted.svelte-1myjzud,h4.variant-highlighted.svelte-1myjzud,h5.variant-highlighted.svelte-1myjzud,h6.variant-highlighted.svelte-1myjzud,p.variant-highlighted.svelte-1myjzud {
    color: var(--variant-default-color)
}

.svelte-1lfzokq .active {
    color: white;
    background-color: var(--blue-500);
}
</style>
