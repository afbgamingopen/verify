<script setup>
import { defineProps, ref, watch, onMounted } from "vue";
import Result from "./roulette-result.vue";
import StakeLoad from "./stakeLoad.vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
const isOpen = ref(false);
onMounted(() => {
  if (
    props.data.clientSeed === "" ||
    props.data.serverSeed === "" ||
    props.data.game === "" ||
    props.data.nonce === 0
  ) {
    isOpen.value = true;
  } else {
    isOpen.value = false;
  }
});
watch(props, () => {
  if (
    props.data.clientSeed === "" ||
    props.data.serverSeed === "" ||
    props.data.game === "" ||
    props.data.nonce === 0
  ) {
    isOpen.value = true;
  } else {
    isOpen.value = false;
  }
});
</script>

<template>
  <div>
    <div class="wrap svelte-q19e8x">
      <StakeLoad v-if="isOpen" />
      <div class="contents" v-else>
        <div class="btnR1">
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="hxImg" src="../assets/rouletteIMG/hx.png" alt="" />
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img8" src="../assets/rouletteIMG/8.png" alt="" />
        </div>
        <div class="btnR2">
          <img src="../assets/rouletteIMG/Even.png" alt="" />
        </div>
        <div class="btnR3 btnRed">
          <img src="../assets/rouletteIMG/red.png" alt="" />
        </div>
        <div class="btnR4 btnRc">
          <img src="../assets/rouletteIMG/hei.png" alt="" />
        </div>
        <div class="btnR5">
          <img src="../assets/rouletteIMG/Odd.png" alt="" />
        </div>
        <div class="btnR6">
          <img class="img1" src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img9" src="../assets/rouletteIMG/9.png" alt="" />
          <img class="hxImg" src="../assets/rouletteIMG/hx.png" alt="" />
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
        </div>
        <div class="countBox"></div>
        <div class="btnR7">
          <div class="btnRImg7">
            <img src="../assets/rouletteIMG/1st.png" alt="" />
          </div>
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
        </div>
        <div class="btnR8">
          <div class="btnRImg8">
            <img src="../assets/rouletteIMG/2nd.png" alt="" />
          </div>
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
        </div>
        <div class="btnR9">
          <div class="btnRImg9">
            <img src="../assets/rouletteIMG/3rd.png" alt="" />
          </div>
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
        </div>
        <div class="countBox"></div>
        <div class="r0" :class="data.finalResult === 0 ? 'countSelect' : ''">
          <img class="img0" src="../assets/rouletteIMG/0.png" alt="" />
        </div>
        <div
          class="count oneTwo18 countOdd oneTwo12 oneTwo1"
          :class="data.finalResult === 1 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
        </div>
        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc oneTwo1Rc"
          :class="data.finalResult === 4 ? 'countSelect' : ''"
        >
          <img class="img4" src="../assets/rouletteIMG/4.png" alt="" />
        </div>
        <div
          class="count oneTwo18 countOdd oneTwo12 oneTwo1"
          :class="data.finalResult === 7 ? 'countSelect' : ''"
        >
          <img class="img7" src="../assets/rouletteIMG/7.png" alt="" />
        </div>
        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc oneTwo1Rc"
          :class="data.finalResult === 10 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img0" src="../assets/rouletteIMG/0.png" alt="" />
        </div>
        <div
          class="countColor oneTwo18Rc countOddRc two24Rc oneTwo1Rc"
          :class="data.finalResult === 13 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
        </div>
        <div
          class="count oneTwo18 countEven two24 oneTwo1"
          :class="data.finalResult === 16 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
        </div>
        <div
          class="count countOdd to36 two24 oneTwo1Rc"
          :class="data.finalResult === 19 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img9" src="../assets/rouletteIMG/9.png" alt="" />
        </div>
        <div
          class="countColor countEvenRc to36Rc two24Rc oneTwo1Rc"
          :class="data.finalResult === 22 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
        </div>
        <div
          class="count countOdd to36 count36 oneTwo1"
          :class="data.finalResult === 25 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img5" src="../assets/rouletteIMG/5.png" alt="" />
        </div>
        <div
          class="countColor countEvenRc to36Rc count36Rc oneTwo1Rc"
          :class="data.finalResult === 28 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img8" src="../assets/rouletteIMG/8.png" alt="" />
        </div>
        <div
          class="countColor countOddRc to36Rc count36Rc oneTwo1Rc"
          :class="data.finalResult === 31 ? 'countSelect' : ''"
        >
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          <img src="../assets/rouletteIMG/1.png" alt="" />
        </div>
        <div
          class="count countEven to36 count36 oneTwo1"
          :class="data.finalResult === 34 ? 'countSelect' : ''"
        >
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          <img class="img4" src="../assets/rouletteIMG/4.png" alt="" />
        </div>
        <div class="countBottom1">
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img_" src="../assets/rouletteIMG/_.png" alt="" />
          <img class="img1" src="../assets/rouletteIMG/1.png" alt="" />
        </div>
        <div class="imgZc1"></div>

        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc to235Rc"
          :class="data.finalResult === 2 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
        </div>
        <div
          class="count oneTwo18 countOdd oneTwo12 to235"
          :class="data.finalResult === 5 ? 'countSelect' : ''"
        >
          <img class="img5" src="../assets/rouletteIMG/5.png" alt="" />
        </div>
        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc to235Rc"
          :class="data.finalResult === 8 ? 'countSelect' : ''"
        >
          <img class="img8" src="../assets/rouletteIMG/8.png" alt="" />
        </div>
        <div
          class="countColor oneTwo18Rc countOddRc oneTwo12Rc to235Rc"
          :class="data.finalResult === 11 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img src="../assets/rouletteIMG/1.png" alt="" />
        </div>
        <div
          class="count oneTwo18 countEven two24 to235"
          :class="data.finalResult === 14 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img4" src="../assets/rouletteIMG/4.png" alt="" />
        </div>
        <div
          class="countColor oneTwo18Rc countOddRc two24Rc to235Rc"
          :class="data.finalResult === 17 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img7" src="../assets/rouletteIMG/7.png" alt="" />
        </div>
        <div
          class="countColor countEvenRc to36Rc two24Rc to235Rc"
          :class="data.finalResult === 20 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img0" src="../assets/rouletteIMG/0.png" alt="" />
        </div>
        <div
          class="count countOdd to36 two24 to235"
          :class="data.finalResult === 23 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
        </div>
        <div
          class="countColor countEvenRc to36Rc count36Rc to235Rc"
          :class="data.finalResult === 26 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
        </div>
        <div
          class="countColor countOddRc to36Rc count36Rc to235Rc"
          :class="data.finalResult === 29 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img9" src="../assets/rouletteIMG/9.png" alt="" />
        </div>
        <div
          class="count countEven to36 count36 to235"
          :class="data.finalResult === 32 ? 'countSelect' : ''"
        >
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
        </div>
        <div
          class="countColor countOddRc to36Rc count36Rc to235Rc"
          :class="data.finalResult === 35 ? 'countSelect' : ''"
        >
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          <img class="img5" src="../assets/rouletteIMG/5.png" alt="" />
        </div>
        <div class="countBottom2">
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img_" src="../assets/rouletteIMG/_.png" alt="" />
          <img class="img1" src="../assets/rouletteIMG/1.png" alt="" />
        </div>
        <div class="imgZc2"></div>

        <div
          class="count oneTwo18 countOdd oneTwo12 to336"
          :class="data.finalResult === 3 ? 'countSelect' : ''"
        >
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
        </div>
        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc to336Rc"
          :class="data.finalResult === 6 ? 'countSelect' : ''"
        >
          <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
        </div>
        <div
          class="count oneTwo18 countOdd oneTwo12 to336"
          :class="data.finalResult === 9 ? 'countSelect' : ''"
        >
          <img class="img9" src="../assets/rouletteIMG/9.png" alt="" />
        </div>
        <div
          class="count oneTwo18 countEven oneTwo12 to336"
          :class="data.finalResult === 12 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
        </div>
        <div
          class="countColor oneTwo18Rc countOddRc two24Rc to336Rc"
          :class="data.finalResult === 15 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img5" src="../assets/rouletteIMG/5.png" alt="" />
        </div>
        <div
          class="count oneTwo18 countEven two24 to336"
          :class="data.finalResult === 18 ? 'countSelect' : ''"
        >
          <img src="../assets/rouletteIMG/1.png" alt="" />
          <img class="img8" src="../assets/rouletteIMG/8.png" alt="" />
        </div>
        <div
          class="count countOdd to36 two24 to336"
          :class="data.finalResult === 21 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img src="../assets/rouletteIMG/1.png" alt="" />
        </div>
        <div
          class="countColor countEvenRc to36Rc two24Rc to336Rc"
          :class="data.finalResult === 24 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img4" src="../assets/rouletteIMG/4.png" alt="" />
        </div>
        <div
          class="count countOdd to36 count36 to336"
          :class="data.finalResult === 27 ? 'countSelect' : ''"
        >
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img7" src="../assets/rouletteIMG/7.png" alt="" />
        </div>
        <div
          class="count countEven to36 count36 to336"
          :class="data.finalResult === 30 ? 'countSelect' : ''"
        >
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          <img class="img0" src="../assets/rouletteIMG/0.png" alt="" />
        </div>
        <div
          class="countColor countOddRc to36Rc count36Rc to336Rc"
          :class="data.finalResult === 33 ? 'countSelect' : ''"
        >
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
        </div>
        <div
          class="count countEven to36 count36 to336"
          :class="data.finalResult === 36 ? 'countSelect' : ''"
        >
          <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
        </div>
        <div class="countBottom3">
          <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          <img class="img_" src="../assets/rouletteIMG/_.png" alt="" />
          <img class="img1" src="../assets/rouletteIMG/1.png" alt="" />
        </div>
        <div class="imgZc3"></div>
        <div class="bottomBgc1">
          <div
            class="count oneTwo1"
            :class="data.finalResult === 1 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 4 ? 'countSelect' : ''"
          >
            <img class="img4" src="../assets/rouletteIMG/4.png" alt="" />
          </div>
          <div
            class="count oneTwo1"
            :class="data.finalResult === 7 ? 'countSelect' : ''"
          >
            <img class="img7" src="../assets/rouletteIMG/7.png" alt="" />
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 10 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img0" src="../assets/rouletteIMG/0.png" alt="" />
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 13 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          </div>
          <div
            class="count oneTwo1"
            :class="data.finalResult === 16 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
          </div>
          <div
            class="count oneTwo1Rc"
            :class="data.finalResult === 19 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img9" src="../assets/rouletteIMG/9.png" alt="" />
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 22 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          </div>
          <div
            class="count oneTwo1"
            :class="data.finalResult === 25 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img5" src="../assets/rouletteIMG/5.png" alt="" />
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 28 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img8" src="../assets/rouletteIMG/8.png" alt="" />
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 31 ? 'countSelect' : ''"
          >
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
            <img src="../assets/rouletteIMG/1.png" alt="" />
          </div>
          <div
            class="count oneTwo1"
            :class="data.finalResult === 34 ? 'countSelect' : ''"
          >
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
            <img class="img4" src="../assets/rouletteIMG/4.png" alt="" />
          </div>
        </div>
        <div class="bottomBgc2">
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 2 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          </div>
          <div
            class="count to235"
            :class="data.finalResult === 5 ? 'countSelect' : ''"
          >
            <img class="img5" src="../assets/rouletteIMG/5.png" alt="" />
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 8 ? 'countSelect' : ''"
          >
            <img class="img8" src="../assets/rouletteIMG/8.png" alt="" />
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 11 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img src="../assets/rouletteIMG/1.png" alt="" />
          </div>
          <div
            class="count to235"
            :class="data.finalResult === 14 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img4" src="../assets/rouletteIMG/4.png" alt="" />
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 17 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img7" src="../assets/rouletteIMG/7.png" alt="" />
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 20 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img0" src="../assets/rouletteIMG/0.png" alt="" />
          </div>
          <div
            class="count to235"
            :class="data.finalResult === 23 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 26 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 29 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img9" src="../assets/rouletteIMG/9.png" alt="" />
          </div>
          <div
            class="count to235"
            :class="data.finalResult === 32 ? 'countSelect' : ''"
          >
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 35 ? 'countSelect' : ''"
          >
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
            <img class="img5" src="../assets/rouletteIMG/5.png" alt="" />
          </div>
        </div>
        <div class="bottomBgc3">
          <div
            class="count oneTwo18 countOdd oneTwo12 to336"
            :class="data.finalResult === 3 ? 'countSelect' : ''"
          >
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          </div>
          <div
            class="countColor oneTwo18Rc countEvenRc oneTwo12Rc to336Rc"
            :class="data.finalResult === 6 ? 'countSelect' : ''"
          >
            <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
          </div>
          <div
            class="count oneTwo18 countOdd oneTwo12 to336"
            :class="data.finalResult === 9 ? 'countSelect' : ''"
          >
            <img class="img9" src="../assets/rouletteIMG/9.png" alt="" />
          </div>
          <div
            class="count oneTwo18 countEven oneTwo12 to336"
            :class="data.finalResult === 12 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
          </div>
          <div
            class="countColor oneTwo18Rc countOddRc two24Rc to336Rc"
            :class="data.finalResult === 15 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img5" src="../assets/rouletteIMG/5.png" alt="" />
          </div>
          <div
            class="count oneTwo18 countEven two24 to336"
            :class="data.finalResult === 18 ? 'countSelect' : ''"
          >
            <img src="../assets/rouletteIMG/1.png" alt="" />
            <img class="img8" src="../assets/rouletteIMG/8.png" alt="" />
          </div>
          <div
            class="count countOdd to36 two24 to336"
            :class="data.finalResult === 21 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img src="../assets/rouletteIMG/1.png" alt="" />
          </div>
          <div
            class="countColor countEvenRc to36Rc two24Rc to336Rc"
            :class="data.finalResult === 24 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img4" src="../assets/rouletteIMG/4.png" alt="" />
          </div>
          <div
            class="count countOdd to36 count36 to336"
            :class="data.finalResult === 27 ? 'countSelect' : ''"
          >
            <img class="img2" src="../assets/rouletteIMG/2.png" alt="" />
            <img class="img7" src="../assets/rouletteIMG/7.png" alt="" />
          </div>
          <div
            class="count countEven to36 count36 to336"
            :class="data.finalResult === 30 ? 'countSelect' : ''"
          >
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
            <img class="img0" src="../assets/rouletteIMG/0.png" alt="" />
          </div>
          <div
            class="countColor countOddRc to36Rc count36Rc to336Rc"
            :class="data.finalResult === 33 ? 'countSelect' : ''"
          >
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
          </div>
          <div
            class="count countEven to36 count36 to336"
            :class="data.finalResult === 36 ? 'countSelect' : ''"
          >
            <img class="img3" src="../assets/rouletteIMG/3.png" alt="" />
            <img class="img6" src="../assets/rouletteIMG/6.png" alt="" />
          </div>
        </div>
      </div>
    </div>
    <Result :data="data" v-if="!isOpen" />
  </div>
</template>


 <style scoped>
.wrap.svelte-q19e8x {
  display: flex;
  justify-content: center;
  width: 100%;
  max-width: 700px;
  border: dotted 2px var(--grey-400);
  padding: 4em 1em 2em;
}
.contents {
  position: relative;
  width: 260px;
  height: 500px;
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  box-sizing: border-box;
}
.countSelect {
  box-shadow: inset 0 0 0 2px #1fff20;
}
.btnR1 {
  width: 15.5%;
  height: 75.5px;
  /* writing-mode: vertical-rl;
  transform: rotate(360deg); */
  text-align: center;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  border-right: 0px solid #06030c;
  cursor: pointer;
  font-weight: 700;
  padding-top: 22px;
  background-color: #4b1f80;
}
.btnR1 img {
  width: 8px;
  vertical-align: bottom;
}
.btnR1 .hxImg {
  transform: translateY(3px);
}
.btnR1 .img8 {
  width: 9px;
}
.btnR1:hover {
  background-color: #8862b9;
}
.btnR1:hover ~ .oneTwo18 {
  background-color: #b76578;
}
.btnR1:hover ~ .oneTwo18Rc {
  background-color: #676a78;
}
.btnR2:hover {
  background-color: #8862b9;
}
.btnR2:hover ~ .countEven {
  background-color: #b76578;
}
.btnR2:hover ~ .countEvenRc {
  background-color: #676a78;
}
.btnR5:hover {
  background-color: #8862b9;
}
.btnR5:hover ~ .countOdd {
  background-color: #b76578;
}
.btnR5:hover ~ .countOddRc {
  background-color: #676a78;
}
.btnR6:hover {
  background-color: #8862b9;
}
.btnR6:hover ~ .to36 {
  background-color: #b76578;
}
.btnR6:hover ~ .to36Rc {
  background-color: #676a78;
}
.btnR7:hover {
  background-color: #8862b9;
}
.btnR7:hover ~ .oneTwo12 {
  background-color: #b76578;
}
.btnR7:hover ~ .oneTwo12Rc {
  background-color: #676a78;
}
.btnR8:hover {
  background-color: #8862b9;
}
.btnR8:hover ~ .two24 {
  background-color: #b76578;
}
.btnR8:hover ~ .two24Rc {
  background-color: #676a78;
}
.btnR9:hover {
  background-color: #8862b9;
}
.btnR9:hover ~ .count36 {
  background-color: #b76578;
}
.btnR9:hover ~ .count36Rc {
  background-color: #676a78;
}

.count:hover {
  background-color: #b76578;
}
.countColor:hover {
  background-color: #676a78;
}
.btnR2 {
  background-color: #4b1f80;
  width: 15.5%;
  height: 75.5px;
  /* writing-mode: vertical-rl;
  transform: rotate(360deg); */
  text-align: center;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  border-right: 0px solid #06030c;
  cursor: pointer;
  font-weight: 700;
  padding-top: 22px;
}
.btnR2 img {
  width: 35px;
  vertical-align: bottom;
}
.btnR3 {
  width: 15.5%;
  height: 75.5px;
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  border-right: 0px solid #06030c;
  /* writing-mode: vertical-rl;
  transform: rotate(360deg); */
  text-align: center;

  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  cursor: pointer;

  font-weight: 700;
  /* background-color: #fe2247; */
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-color: #4b1f80;
}
.btnR3 img {
  width: 25px;
  margin: auto;
}

.btnR4 {
  width: 15.5%;
  height: 75.5px;
  /* writing-mode: vertical-rl;
  transform: rotate(360deg); */
  text-align: center;

  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  cursor: pointer;

  font-weight: 700;
  /* background-color: #2f4553; */
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  border-right: 0px solid #06030c;
  display: flex;
  flex-direction: column;
  justify-content: center;
  background-color: #4b1f80;
}
.btnR4 img {
  width: 25px;
  margin: auto;
}

.lRc1 {
  width: 20px;
  margin-left: 50%;
  transform: translate(-50%, 3%);
  border-top: 0px solid transparent;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-bottom: 20px solid #2f4553;
}
.lRc2 {
  width: 20px;
  margin-left: 50%;
  transform: translateX(-50%);
  border-bottom: 0px solid transparent;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-top: 20px solid #2f4553;
}
.btnR5 {
  width: 15.5%;
  height: 75.5px;
  text-align: center;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  border-right: 0px solid #06030c;
  cursor: pointer;
  font-weight: 700;
  padding-top: 23px;
  background-color: #4b1f80;
}
.btnR5 img {
  width: 34px;
  vertical-align: bottom;
}
.btnR6 {
  width: 15.5%;
  height: 75.5px;
  /* writing-mode: vertical-rl;
  transform: rotate(360deg); */
  text-align: center;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font: inherit;
  vertical-align: baseline;
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  border-right: 0px solid #06030c;
  cursor: pointer;

  font-weight: 700;
  background-color: #4b1f80;
  padding-top: 22px;
}
.btnR6 img {
  width: 7px;
  vertical-align: bottom;
}
.btnR6 .hxImg {
  transform: translateY(3px);
}
.btnR6 .img1 {
  width: 6px;
}
.btnR6 .img3 {
  width: 8px;
}
.btnR6 .img6 {
  width: 8px;
}
.btnRed:hover {
  background-color: #8862b9;
}
.btnRed:hover .lRed1 {
  border-bottom: 20px solid #b76578;
}
.btnRed:hover .lRed2 {
  border-top: 20px solid #b76578;
}
.btnRed:hover ~ .count {
  background-color: #b76578;
}
.btnRc:hover {
  background-color: #8862b9;
}
.btnRc:hover .lRc1 {
  border-bottom: 20px solid #676a78;
}
.btnRc:hover .lRc2 {
  border-top: 20px solid #676a78;
}
.btnRc:hover ~ .countColor {
  background-color: #676a78;
}
.btnR7 {
  width: 15.5%;
  height: 151px;
  color: #000;
  text-align: center;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font: inherit;
  vertical-align: baseline;
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  position: relative;
  cursor: pointer;

  font-weight: 700;
  padding-top: 50px;
  background-color: #4b1f80;
}
.btnR7 img {
  width: 9px;
}
.btnR7 .img2 {
  width: 11px;
}
.btnRImg7 img {
  width: 28px;
}
.btnR8 {
  width: 15.5%;
  height: 151px;
  color: #000;
  text-align: center;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font: inherit;
  vertical-align: baseline;

  position: relative;
  cursor: pointer;
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  font-weight: 700;
  padding-top: 50px;
  background-color: #4b1f80;
}
.btnR8 img {
  width: 9px;
}
.btnR8 .img2 {
  width: 11px;
}
.btnRImg8 img {
  width: 34px;
}
.btnR9 {
  width: 15.5%;
  height: 151px;
  color: #000;
  text-align: center;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font: inherit;
  vertical-align: baseline;
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  position: relative;
  cursor: pointer;
  font-weight: 700;
  padding-top: 50px;
  background-color: #4b1f80;
}
.btnR9 img {
  width: 9px;
}
.btnR9 .img2 {
  width: 11px;
}
.btnRImg9 img {
  width: 34px;
}
.count {
  /* border-left: 1px solid #06030c;
  border-bottom: 1px solid #06030c; */
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  border-right: 0.5px solid #06030c;
  /* width: 23%; */
  height: 7.55%;
  background-color: #8b1e39;
  cursor: pointer;
  overflow: hidden;
  text-align: center;
  line-height: 3.5;
}
.count img {
  width: 11px;
}
.count .img0 {
  width: 13.5px;
}
.count .img2 {
  width: 14px;
}
.count .img4 {
  width: 13px;
}
.count .img6 {
  width: 13px;
}
.count .img8 {
  width: 12.5px;
}
.count .img5 {
  width: 12px;
}
.count .img7 {
  width: 12.5px;
}
.count .img3 {
  width: 14px;
}
.count .img9 {
  width: 13px;
}

.countColor {
  /* border-left: 1px solid #06030c;
  border-bottom: 1px solid #06030c; */
  /*box-shadow: inset 0 0 0 1px #06030c;*/
  border: 1px solid #06030c;
  /* width: 23%; */
  height: 7.55%;
  text-align: center;
  background-color: #252a3e;
  cursor: pointer;
  overflow: hidden;
  border-right: 0.5px solid #06030c;
  text-align: center;
  line-height: 3.5;
}
.countColor img {
  width: 11px;
}
.countColor .img0 {
  width: 13.5px;
}
.countColor .img2 {
  width: 14px;
}
.countColor .img4 {
  width: 14px;
}
.countColor .img6 {
  width: 13px;
}
.countColor .img8 {
  width: 12.5px;
}
.countColor .img5 {
  width: 12.5px;
}
.countColor .img7 {
  width: 12.5px;
}
.countColor .img3 {
  width: 14px;
}
.countColor .img9 {
  width: 13px;
}

.bottomBgc1 .count {
  box-sizing: border-box;
  width: 100%;
  height: 8.3%;
  text-align: center;
  border: 1px solid #06030c;
  border-right: 0.5px solid #06030c;
  background-color: #8862b9;
}
.bottomBgc1 .count img {
  width: 11px;
}
.bottomBgc1 .count .img0 {
  width: 13.5px;
}
.bottomBgc1 .count .img2 {
  width: 14px;
}
.bottomBgc1 .count .img4 {
  width: 13px;
}
.bottomBgc1 .count .img6 {
  width: 13px;
}
.bottomBgc1 .count .img8 {
  width: 12.5px;
}
.bottomBgc1 .count .img5 {
  width: 12px;
}
.bottomBgc1 .count .img7 {
  width: 12.5px;
}
.bottomBgc1 .count .img3 {
  width: 14px;
}
.bottomBgc1 .count .img9 {
  width: 13px;
}

.bottomBgc1 .countColor {
  box-sizing: border-box;
  width: 100%;
  height: 8.3%;
  text-align: center;
  border: 1px solid #06030c;
  border-right: 0.5px solid #06030c;
  background-color: #676a78;
}
.bottomBgc1 .countColor img {
  width: 11px;
}
.bottomBgc1 .countColor .img0 {
  width: 13.5px;
}
.bottomBgc1 .countColor .img2 {
  width: 14px;
}
.bottomBgc1 .countColor .img4 {
  width: 14px;
}
.bottomBgc1 .countColor .img6 {
  width: 13px;
}
.bottomBgc1 .countColor .img8 {
  width: 12.5px;
}
.bottomBgc1 .countColor .img5 {
  width: 12.5px;
}
.bottomBgc1 .countColor .img7 {
  width: 12.5px;
}
.bottomBgc1 .countColor .img3 {
  width: 14px;
}
.bottomBgc1 .countColor .img9 {
  width: 13px;
}
.bottomBgc2 .count {
  box-sizing: border-box;
  width: 100%;
  height: 8.3%;
  text-align: center;
  border: 1px solid #06030c;
  border-right: 0.5px solid #06030c;
  background-color: #8862b9;
}
.bottomBgc2 .count img {
  width: 11px;
}
.bottomBgc2 .count .img0 {
  width: 13.5px;
}
.bottomBgc2 .count .img2 {
  width: 14px;
}
.bottomBgc2 .count .img4 {
  width: 13px;
}
.bottomBgc2 .count .img6 {
  width: 13px;
}
.bottomBgc2 .count .img8 {
  width: 12.5px;
}
.bottomBgc2 .count .img5 {
  width: 12px;
}
.bottomBgc2 .count .img7 {
  width: 12.5px;
}
.bottomBgc2 .count .img3 {
  width: 14px;
}
.bottomBgc2 .count .img9 {
  width: 13px;
}

.bottomBgc2 .countColor {
  box-sizing: border-box;
  width: 100%;
  height: 8.3%;
  text-align: center;
  border: 1px solid #06030c;
  border-right: 0.5px solid #06030c;
  background-color: #676a78;
}
.bottomBgc2 .countColor img {
  width: 11px;
}
.bottomBgc2 .countColor .img0 {
  width: 13.5px;
}
.bottomBgc2 .countColor .img2 {
  width: 14px;
}
.bottomBgc2 .countColor .img4 {
  width: 14px;
}
.bottomBgc2 .countColor .img6 {
  width: 13px;
}
.bottomBgc2 .countColor .img8 {
  width: 12.5px;
}
.bottomBgc2 .countColor .img5 {
  width: 12.5px;
}
.bottomBgc2 .countColor .img7 {
  width: 12.5px;
}
.bottomBgc2 .countColor .img3 {
  width: 14px;
}
.bottomBgc2 .countColor .img9 {
  width: 13px;
}
.bottomBgc3 .count {
  box-sizing: border-box;
  width: 100%;
  height: 8.3%;
  text-align: center;
  border: 1px solid #06030c;
  border-right: 0.5px solid #06030c;
  background-color: #8862b9;
}

.bottomBgc3 .count img {
  width: 11px;
}
.bottomBgc3 .count .img0 {
  width: 13.5px;
}
.bottomBgc3 .count .img2 {
  width: 14px;
}
.bottomBgc3 .count .img4 {
  width: 13px;
}
.bottomBgc3 .count .img6 {
  width: 13px;
}
.bottomBgc3 .count .img8 {
  width: 12.5px;
}
.bottomBgc3 .count .img5 {
  width: 12px;
}
.bottomBgc3 .count .img7 {
  width: 12.5px;
}
.bottomBgc3 .count .img3 {
  width: 14px;
}
.bottomBgc3 .count .img9 {
  width: 13px;
}
.bottomBgc3 .countColor {
  box-sizing: border-box;
  width: 100%;
  height: 8.3%;
  text-align: center;
  border: 1px solid #06030c;
  border-right: 0.5px solid #06030c;
  background-color: #676a78;
}
.bottomBgc3 .countColor img {
  width: 11px;
}
.bottomBgc3 .countColor .img0 {
  width: 13.5px;
}
.bottomBgc3 .countColor .img2 {
  width: 14px;
}
.bottomBgc3 .countColor .img4 {
  width: 14px;
}
.bottomBgc3 .countColor .img6 {
  width: 13px;
}
.bottomBgc3 .countColor .img8 {
  width: 12.5px;
}
.bottomBgc3 .countColor .img5 {
  width: 12.5px;
}
.bottomBgc3 .countColor .img7 {
  width: 12.5px;
}
.bottomBgc3 .countColor .img3 {
  width: 14px;
}
.bottomBgc3 .countColor .img9 {
  width: 13px;
}
.countBl {
  width: 23%;
  height: 6.7%;
  text-align: center;
  margin-top: 2%;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  box-shadow: inset 0 0 0 1.5px #2f4553;
  font-weight: 700;

  color: #fff;
  cursor: pointer;
}
.r0 {
  position: absolute;
  right: 0%;
  top: -7.2%;
  width: 69%;
  height: 7.1%;
  background-color: #419e3f;
  text-align: center;
  font-weight: 700;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  cursor: pointer;
  background-color: #4b1f80;
  border: 1px solid #06030c;
  line-height: 3.3;
}
.r0:hover {
  background-color: #8862b9;
}
.r0 img {
  width: 13px;
}
.countBottom1 {
  width: 23%;
  height: 7%;
  text-align: center;
  font-weight: 700;
  color: #fff;
  cursor: pointer;
  border-bottom: 0;
  line-height: 2.5;
  background-color: #4b1f80;
  border: 1px solid #06030c;
  border-bottom: 1px solid transparent;
}
.countBottom1 img {
  width: 14px;
  vertical-align: bottom;
}
.countBottom1 .img_ {
  width: 7px;
  vertical-align: bottom;
  transform: translateY(2px);
}
.countBottom1 .img1 {
  width: 11px;
}
.countBottom2 {
  width: 23%;
  height: 7%;
  text-align: center;
  font-weight: 700;
  color: #fff;
  cursor: pointer;
  line-height: 2.5;
  background-color: #4b1f80;
  border: 1px solid #06030c;
  border-bottom: 1px solid transparent;
}
.countBottom2 img {
  width: 14px;
  vertical-align: bottom;
}
.countBottom2 .img_ {
  width: 7px;
  vertical-align: bottom;
  transform: translateY(2px);
}
.countBottom2 .img1 {
  width: 11px;
}
.countBottom3 {
  width: 23%;
  height: 7%;
  text-align: center;
  /* text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3); */
  /* box-shadow: inset 0 0 0 1.5px #2f4553; */
  font-weight: 700;
  color: #fff;
  cursor: pointer;
  background-color: #4b1f80;
  line-height: 2.5;
  border: 1px solid #06030c;
  border-bottom: 1px solid transparent;
}
.countBottom3 img {
  width: 14px;
  vertical-align: bottom;
}
.countBottom3 .img_ {
  width: 7px;
  vertical-align: bottom;
  transform: translateY(2px);
}
.countBottom3 .img1 {
  width: 11px;
}
.imgZc1 {
  border-top: 12px solid #4b1f80;
  border-right: 29px solid transparent;
  border-bottom: 0px solid transparent;
  border-left: 30px solid transparent;
  transform: translateY(-1px);
}
.imgZc2 {
  border-top: 12px solid #4b1f80;
  border-right: 29px solid transparent;
  border-bottom: 0px solid transparent;
  border-left: 30px solid transparent;
  transform: translateY(-1px);
}
.imgZc3 {
  border-top: 12px solid #4b1f80;
  border-right: 29px solid transparent;
  border-bottom: 0px solid transparent;
  border-left: 30px solid transparent;
  transform: translateY(-1px);
}
.bottomS {
  position: absolute;
  top: 0;
  left: 0;
  border: 30px;
  border-top: 30px solid yellow;
  border-left: 10px solid transparent;
  border-right: 10px solid transparent;
  border-bottom: 30px solid transparent;
}
.countBox {
  width: 15%;
  height: 41px;
}
.countBottom1:hover {
  background-color: #8862b9;
}
.countBottom1:hover ~ .imgZc1 {
  border-top: 11px solid #8862b9;
}
.countBottom1:hover ~ .oneTwo1 {
  background-color: #b76578 !important;
}
.countBottom1:hover ~ .oneTwo1Rc {
  background-color: #676a78;
}
.countBottom2:hover {
  background-color: #8862b9;
}
.countBottom2:hover ~ .imgZc2 {
  border-top: 11px solid #8862b9;
}
.countBottom2:hover ~ .to235 {
  background-color: #b76578;
}
.countBottom2:hover ~ .to235Rc {
  background-color: #676a78;
}
.countBottom3:hover {
  background-color: #8862b9;
}
.countBottom3:hover ~ .imgZc3 {
  border-top: 11px solid #8862b9;
}
.countBottom3:hover ~ .to336 {
  background-color: #b76578;
}
.countBottom3:hover ~ .to336Rc {
  background-color: #676a78;
}
.bottomBgc1 {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  position: absolute;
  right: 46%;
  top: 0;
  width: 23.1%;
  height: 91%;
  opacity: 0;
  display: none;
}
.countBottom1:hover ~ .bottomBgc1 {
  opacity: 1;
  display: block;
}
.bottomBgc2 {
  position: absolute;
  right: 23%;
  top: 0;
  width: 23%;
  height: 91%;
  opacity: 0;
  display: none;
}
.countBottom2:hover ~ .bottomBgc2 {
  opacity: 1;
  display: block;
}
.bottomBgc3 {
  position: absolute;
  right: 0%;
  top: 0;
  width: 23%;
  height: 91%;
  opacity: 0;
  display: none;
}
.countBottom3:hover ~ .bottomBgc3 {
  opacity: 1;
  display: block;
}
img {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  pointer-events: none !important;
}
img:active {
  -webkit-transform: scale(1);
}
</style>
