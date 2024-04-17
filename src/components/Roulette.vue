<script setup>
import { defineProps } from "vue";
import Result from "./roulette-result.vue";
const props = defineProps({ data: { type: Object } });
const data = props.data;
</script>

<template>
  <div>
    <div class="wrap svelte-q19e8x">
      <div class="contents">
        <div class="btnR1">1 to 18</div>
        <div class="btnR2">Even</div>
        <div class="btnR3 btnRed"></div>
        <div class="btnR4 btnRc"></div>
        <div class="btnR5">Odd</div>
        <div class="btnR6">19 to 36</div>
        <div class="countBox"></div>
        <div class="btnR7">1 to 12</div>
        <div class="btnR8">13 to 24</div>
        <div class="btnR9">25 to 36</div>
        <div class="countBox"></div>
        <div class="r0">0</div>
        <div
          class="count oneTwo18 countOdd oneTwo12 oneTwo1"
          :class="data.finalResult === 1 ? 'countSelect' : ''"
        >
          1
        </div>
        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc oneTwo1Rc"
          :class="data.finalResult === 4 ? 'countSelect' : ''"
        >
          4
        </div>
        <div
          class="count oneTwo18 countOdd oneTwo12 oneTwo1"
          :class="data.finalResult === 7 ? 'countSelect' : ''"
        >
          7
        </div>
        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc oneTwo1Rc"
          :class="data.finalResult === 10 ? 'countSelect' : ''"
        >
          10
        </div>
        <div
          class="countColor oneTwo18Rc countOddRc two24Rc oneTwo1Rc"
          :class="data.finalResult === 13 ? 'countSelect' : ''"
        >
          13
        </div>
        <div
          class="count oneTwo18 countEven two24 oneTwo1"
          :class="data.finalResult === 16 ? 'countSelect' : ''"
        >
          16
        </div>
        <div
          class="count countOdd to36 two24 oneTwo1Rc"
          :class="data.finalResult === 19 ? 'countSelect' : ''"
        >
          19
        </div>
        <div
          class="countColor countEvenRc to36Rc two24Rc oneTwo1Rc"
          :class="data.finalResult === 22 ? 'countSelect' : ''"
        >
          22
        </div>
        <div
          class="count countOdd to36 count36 oneTwo1"
          :class="data.finalResult === 25 ? 'countSelect' : ''"
        >
          25
        </div>
        <div
          class="countColor countEvenRc to36Rc count36Rc oneTwo1Rc"
          :class="data.finalResult === 28 ? 'countSelect' : ''"
        >
          28
        </div>
        <div
          class="countColor countOddRc to36Rc count36Rc oneTwo1Rc"
          :class="data.finalResult === 31 ? 'countSelect' : ''"
        >
          31
        </div>
        <div
          class="count countEven to36 count36 oneTwo1"
          :class="data.finalResult === 34 ? 'countSelect' : ''"
        >
          34
        </div>
        <div class="countBottom1">2:1</div>

        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc to235Rc"
          :class="data.finalResult === 2 ? 'countSelect' : ''"
        >
          2
        </div>
        <div
          class="count oneTwo18 countOdd oneTwo12 to235"
          :class="data.finalResult === 5 ? 'countSelect' : ''"
        >
          5
        </div>
        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc to235Rc"
          :class="data.finalResult === 8 ? 'countSelect' : ''"
        >
          8
        </div>
        <div
          class="countColor oneTwo18Rc countOddRc oneTwo12Rc to235Rc"
          :class="data.finalResult === 11 ? 'countSelect' : ''"
        >
          11
        </div>
        <div
          class="count oneTwo18 countEven two24 to235"
          :class="data.finalResult === 14 ? 'countSelect' : ''"
        >
          14
        </div>
        <div
          class="countColor oneTwo18Rc countOddRc two24Rc to235Rc"
          :class="data.finalResult === 17 ? 'countSelect' : ''"
        >
          17
        </div>
        <div
          class="countColor countEvenRc to36Rc two24Rc to235Rc"
          :class="data.finalResult === 20 ? 'countSelect' : ''"
        >
          20
        </div>
        <div
          class="count countOdd to36 two24 to235"
          :class="data.finalResult === 23 ? 'countSelect' : ''"
        >
          23
        </div>
        <div
          class="countColor countEvenRc to36Rc count36Rc to235Rc"
          :class="data.finalResult === 26 ? 'countSelect' : ''"
        >
          26
        </div>
        <div
          class="countColor countOddRc to36Rc count36Rc to235Rc"
          :class="data.finalResult === 29 ? 'countSelect' : ''"
        >
          29
        </div>
        <div
          class="count countEven to36 count36 to235"
          :class="data.finalResult === 32 ? 'countSelect' : ''"
        >
          32
        </div>
        <div
          class="countColor countOddRc to36Rc count36Rc to235Rc"
          :class="data.finalResult === 35 ? 'countSelect' : ''"
        >
          35
        </div>
        <div class="countBottom2">2:1</div>

        <div
          class="count oneTwo18 countOdd oneTwo12 to336"
          :class="data.finalResult === 3 ? 'countSelect' : ''"
        >
          3
        </div>
        <div
          class="countColor oneTwo18Rc countEvenRc oneTwo12Rc to336Rc"
          :class="data.finalResult === 6 ? 'countSelect' : ''"
        >
          6
        </div>
        <div
          class="count oneTwo18 countOdd oneTwo12 to336"
          :class="data.finalResult === 9 ? 'countSelect' : ''"
        >
          9
        </div>
        <div
          class="count oneTwo18 countEven oneTwo12 to336"
          :class="data.finalResult === 12 ? 'countSelect' : ''"
        >
          12
        </div>
        <div
          class="countColor oneTwo18Rc countOddRc two24Rc to336Rc"
          :class="data.finalResult === 15 ? 'countSelect' : ''"
        >
          15
        </div>
        <div
          class="count oneTwo18 countEven two24 to336"
          :class="data.finalResult === 18 ? 'countSelect' : ''"
        >
          18
        </div>
        <div
          class="count countOdd to36 two24 to336"
          :class="data.finalResult === 21 ? 'countSelect' : ''"
        >
          21
        </div>
        <div
          class="countColor countEvenRc to36Rc two24Rc to336Rc"
          :class="data.finalResult === 24 ? 'countSelect' : ''"
        >
          24
        </div>
        <div
          class="count countOdd to36 count36 to336"
          :class="data.finalResult === 27 ? 'countSelect' : ''"
        >
          27
        </div>
        <div
          class="count countEven to36 count36 to336"
          :class="data.finalResult === 30 ? 'countSelect' : ''"
        >
          30
        </div>
        <div
          class="countColor countOddRc to36Rc count36Rc to336Rc"
          :class="data.finalResult === 33 ? 'countSelect' : ''"
        >
          33
        </div>
        <div
          class="count countEven to36 count36 to336"
          :class="data.finalResult === 36 ? 'countSelect' : ''"
        >
          36
        </div>
        <div class="countBottom3">2:1</div>
        <div class="bottomBgc1">
          <div
            class="count oneTwo1"
            :class="data.finalResult === 1 ? 'countSelect' : ''"
          >
            1
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 4 ? 'countSelect' : ''"
          >
            4
          </div>
          <div
            class="count oneTwo1"
            :class="data.finalResult === 7 ? 'countSelect' : ''"
          >
            7
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 10 ? 'countSelect' : ''"
          >
            10
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 13 ? 'countSelect' : ''"
          >
            13
          </div>
          <div
            class="count oneTwo1"
            :class="data.finalResult === 16 ? 'countSelect' : ''"
          >
            16
          </div>
          <div
            class="count oneTwo1Rc"
            :class="data.finalResult === 19 ? 'countSelect' : ''"
          >
            19
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 22 ? 'countSelect' : ''"
          >
            22
          </div>
          <div
            class="count oneTwo1"
            :class="data.finalResult === 25 ? 'countSelect' : ''"
          >
            25
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 28 ? 'countSelect' : ''"
          >
            28
          </div>
          <div
            class="countColor oneTwo1Rc"
            :class="data.finalResult === 31 ? 'countSelect' : ''"
          >
            31
          </div>
          <div
            class="count oneTwo1"
            :class="data.finalResult === 34 ? 'countSelect' : ''"
          >
            34
          </div>
        </div>
        <div class="bottomBgc2">
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 2 ? 'countSelect' : ''"
          >
            2
          </div>
          <div
            class="count to235"
            :class="data.finalResult === 5 ? 'countSelect' : ''"
          >
            5
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 8 ? 'countSelect' : ''"
          >
            8
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 11 ? 'countSelect' : ''"
          >
            11
          </div>
          <div
            class="count to235"
            :class="data.finalResult === 14 ? 'countSelect' : ''"
          >
            14
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 17 ? 'countSelect' : ''"
          >
            17
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 20 ? 'countSelect' : ''"
          >
            20
          </div>
          <div
            class="count to235"
            :class="data.finalResult === 23 ? 'countSelect' : ''"
          >
            23
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 26 ? 'countSelect' : ''"
          >
            26
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 29 ? 'countSelect' : ''"
          >
            29
          </div>
          <div
            class="count to235"
            :class="data.finalResult === 32 ? 'countSelect' : ''"
          >
            32
          </div>
          <div
            class="countColor to235Rc"
            :class="data.finalResult === 35 ? 'countSelect' : ''"
          >
            35
          </div>
        </div>
        <div class="bottomBgc3">
          <div
            class="count oneTwo18 countOdd oneTwo12 to336"
            :class="data.finalResult === 3 ? 'countSelect' : ''"
          >
            3
          </div>
          <div
            class="countColor oneTwo18Rc countEvenRc oneTwo12Rc to336Rc"
            :class="data.finalResult === 6 ? 'countSelect' : ''"
          >
            6
          </div>
          <div
            class="count oneTwo18 countOdd oneTwo12 to336"
            :class="data.finalResult === 9 ? 'countSelect' : ''"
          >
            9
          </div>
          <div
            class="count oneTwo18 countEven oneTwo12 to336"
            :class="data.finalResult === 12 ? 'countSelect' : ''"
          >
            12
          </div>
          <div
            class="countColor oneTwo18Rc countOddRc two24Rc to336Rc"
            :class="data.finalResult === 15 ? 'countSelect' : ''"
          >
            15
          </div>
          <div
            class="count oneTwo18 countEven two24 to336"
            :class="data.finalResult === 18 ? 'countSelect' : ''"
          >
            18
          </div>
          <div
            class="count countOdd to36 two24 to336"
            :class="data.finalResult === 21 ? 'countSelect' : ''"
          >
            21
          </div>
          <div
            class="countColor countEvenRc to36Rc two24Rc to336Rc"
            :class="data.finalResult === 24 ? 'countSelect' : ''"
          >
            24
          </div>
          <div
            class="count countOdd to36 count36 to336"
            :class="data.finalResult === 27 ? 'countSelect' : ''"
          >
            27
          </div>
          <div
            class="count countEven to36 count36 to336"
            :class="data.finalResult === 30 ? 'countSelect' : ''"
          >
            30
          </div>
          <div
            class="countColor countOddRc to36Rc count36Rc to336Rc"
            :class="data.finalResult === 33 ? 'countSelect' : ''"
          >
            33
          </div>
          <div
            class="count countEven to36 count36 to336"
            :class="data.finalResult === 36 ? 'countSelect' : ''"
          >
            36
          </div>
        </div>
      </div>
    </div>
    <Result :data="data" />
  </div>
</template>


 <style scoped>
.wrap.svelte-q19e8x {
  display: flex;
  justify-content: center;
  width: 100%;
  max-width: 700px;
  border: dotted 2px var(--grey-400);
  padding: 3.5em 1em 1em;
}
.contents {
  position: relative;
  width: 230px;
  height: 450px;
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
}
.countSelect {
  box-shadow: inset 0 0 0 2px #1fff20;
}
.btnR1 {
  width: 15%;
  height:66px;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  cursor: pointer;
  line-height: 2.8;
  font-weight: 700;
  margin-bottom: 1.5%;
}
.btnR1:hover {
  background-color: rgba(47, 69, 83, 1);
}
.btnR1:hover ~ .oneTwo18 {
  background-color: rgba(254, 110, 134, 1);
}
.btnR1:hover ~ .oneTwo18Rc {
  background-color: rgba(75, 110, 132, 1);
}
.btnR2:hover {
  background-color: rgba(47, 69, 83, 1);
}
.btnR2:hover ~ .countEven {
  background-color: rgba(254, 110, 134, 1);
}
.btnR2:hover ~ .countEvenRc {
  background-color: rgba(75, 110, 132, 1);
}
.btnR5:hover {
  background-color: rgba(47, 69, 83, 1);
}
.btnR5:hover ~ .countOdd {
  background-color: rgba(254, 110, 134, 1);
}
.btnR5:hover ~ .countOddRc {
  background-color: rgba(75, 110, 132, 1);
}
.btnR6:hover {
  background-color: rgba(47, 69, 83, 1);
}
.btnR6:hover ~ .to36 {
  background-color: rgba(254, 110, 134, 1);
}
.btnR6:hover ~ .to36Rc {
  background-color: rgba(75, 110, 132, 1);
}
.btnR7:hover {
  background-color: rgba(47, 69, 83, 1);
}
.btnR7:hover ~ .oneTwo12 {
  background-color: rgba(254, 110, 134, 1);
}
.btnR7:hover ~ .oneTwo12Rc {
  background-color: rgba(75, 110, 132, 1);
}
.btnR8:hover {
  background-color: rgba(47, 69, 83, 1);
}
.btnR8:hover ~ .two24 {
  background-color: rgba(254, 110, 134, 1);
}
.btnR8:hover ~ .two24Rc {
  background-color: rgba(75, 110, 132, 1);
}
.btnR9:hover {
  background-color: rgba(47, 69, 83, 1);
}
.btnR9:hover ~ .count36 {
  background-color: rgba(254, 110, 134, 1);
}
.btnR9:hover ~ .count36Rc {
  background-color: rgba(75, 110, 132, 1);
}

.count:hover {
  background-color: rgba(254, 110, 134, 1);
}
.countColor:hover {
  background-color: rgba(75, 110, 132, 1);
}
.btnR2 {
  width: 15%;
  height:66px;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  cursor: pointer;
  font-weight: 700;
  margin-bottom: 1.5%;
  line-height: 2.8;
}
.btnR3 {
  width: 15%;
  height: 66px;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  cursor: pointer;
  line-height: 2.8;
  font-weight: 700;
  background-color: #fe2247;
  margin-bottom: 1.5%;
}
.btnR4 {
  width: 15%;
  height: 66px;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  cursor: pointer;
  line-height: 2.8;
  font-weight: 700;
  background-color: #2f4553;
  margin-bottom: 1.5%;
}
.btnR5 {
  width: 15%;
  height: 66px;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 600;
  font: inherit;
  vertical-align: baseline;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  cursor: pointer;
  line-height: 2.8;
  font-weight: 700;
  margin-bottom: 1.5%;
}
.btnR6 {
  width: 15%;
  height: 66px;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font: inherit;
  vertical-align: baseline;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  cursor: pointer;
  line-height: 2.8;
  font-weight: 700;
  margin-bottom: 1.5%;
}
.btnRed:hover {
  background-color: rgba(254, 110, 134, 1);
}
.btnRed:hover ~ .count {
  background-color: rgba(254, 110, 134, 1);
}
.btnRc:hover {
  background-color: rgba(75, 110, 132, 1);
}
.btnRc:hover ~ .countColor {
  background-color: rgba(75, 110, 132, 1);
}
.btnR7 {
  width: 15%;
  height:135.5px;
  color: #000;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font: inherit;
  vertical-align: baseline;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  position: relative;
  cursor: pointer;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  line-height: 2.8;
  font-weight: 700;
  margin-bottom: 1.5%;
}
.btnR8 {
  width: 15%;
  height: 135.5px;
  color: #000;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font: inherit;
  vertical-align: baseline;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  position: relative;
  cursor: pointer;
  box-shadow: inset 0 0 0 1.5px #2f4553;

  line-height: 2.8;
  font-weight: 700;
  margin-bottom: 1.5%;
}
.btnR9 {
  width: 15%;
  height: 135.5px;
  color: #000;
  writing-mode: vertical-rl;
  transform: rotate(360deg);
  text-align: center;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font: inherit;
  vertical-align: baseline;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  position: relative;
  box-shadow: inset 0 0 0 1.5px #2f4553;
  cursor: pointer;
  line-height: 2.8;
  font-weight: 700;
}
.count {
  width: 21%;
  height: 6.7%;
  text-align: center;
  line-height: 2.4;
  background-color: #fe2247;
  margin-bottom: 2%;
  border-radius: 3px;
  margin-left: 1%;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 700;
  cursor: pointer;
}
.countColor {
  width: 21%;
  height: 6.7%;
  margin-left: 1%;
  text-align: center;
  line-height: 2.4;
  background-color: #2f4553;
  margin-bottom: 2%;
  border-radius: 3px;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  font-weight: 700;
  cursor: pointer;
}

.bottomBgc1 .count {
  width: 100%;
  height: 7.4%;
  text-align: center;
  margin-bottom: 8.5%;
  background-color: rgba(254, 110, 134, 1);
  border-radius: 3px;
}
.bottomBgc1 .countColor {
  width: 100%;
  height: 7.4%;
  text-align: center;
  background-color: rgba(75, 110, 132, 1);
  border-radius: 3px;
  margin-bottom: 8.5%;
}
.bottomBgc2 .count {
  width: 100%;
  height: 7.4%;
  text-align: center;
  margin-bottom: 8.5%;
  background-color: rgba(254, 110, 134, 1);
  border-radius: 3px;
}
.bottomBgc2 .countColor {
  width: 100%;
  height: 7.4%;
  text-align: center;
  background-color: rgba(75, 110, 132, 1);
  border-radius: 3px;
  margin-bottom: 8.5%;
}
.bottomBgc3 .count {
  width: 100%;
  height: 7.4%;
  text-align: center;
  margin-bottom: 8.5%;
  background-color: rgba(254, 110, 134, 1);
  border-radius: 3px;
}
.bottomBgc3 .countColor {
  width: 100%;
  height: 7.4%;
  text-align: center;
  background-color: rgba(75, 110, 132, 1);
  border-radius: 3px;
  margin-bottom: 8.5%;
}
.countBl {
  width: 21%;
  height: 6.7%;
  text-align: center;
  line-height: 2;
  margin-top: 2%;
  margin-left: 1%;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  box-shadow: inset 0 0 0 1.5px #2f4553;
  font-weight: 700;
  border-radius: 3px;
  color: #fff;
  cursor: pointer;
}
.r0 {
  position: absolute;
  right: 1%;
  top: -8.1%;
  width: 67%;
  height: 7.1%;
  line-height: 2.4;
  background-color: #419e3f;
  text-align: center;
  font-weight: 700;
  border-radius: 3px;
  color: #fff;
  white-space: nowrap;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  cursor: pointer;
}
.r0:hover {
  background-color: rgba(105, 194, 103, 1);
}
.countBottom1 {
  width: 21%;
  height: 6.7%;
  margin-left: 1%;
  text-align: center;
  line-height: 2.4;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  box-shadow: inset 0 0 0 1.5px #2f4553;
  font-weight: 700;
  border-radius: 3px;
  color: #fff;
  cursor: pointer;
}
.countBottom2 {
  width: 21%;
  height: 6.7%;
  margin-left: 1%;
  text-align: center;
  line-height: 2.4;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  box-shadow: inset 0 0 0 1.5px #2f4553;
  font-weight: 700;
  border-radius: 3px;
  color: #fff;
  cursor: pointer;
}
.countBottom3 {
  width: 21%;
  height: 6.7%;
  margin-left: 1%;
  text-align: center;
  line-height: 2.4;
  text-shadow: 0 2px 4px rgba(0, 0, 0, 0.3);
  box-shadow: inset 0 0 0 1.5px #2f4553;
  font-weight: 700;
  border-radius: 3px;
  color: #fff;
  cursor: pointer;
}
.countBox {
  width: 15%;
  height: 31.5px;
}
.countBottom1:hover {
  background-color: rgba(47, 69, 83, 1);
}
.countBottom1:hover ~ .oneTwo1 {
  background-color: rgba(254, 110, 134, 1) !important;
}
.countBottom1:hover ~ .oneTwo1Rc {
  background-color: rgba(75, 110, 132, 1);
}
.countBottom2:hover {
  background-color: rgba(47, 69, 83, 1);
}
.countBottom2:hover ~ .to235 {
  background-color: rgba(254, 110, 134, 1);
}
.countBottom2:hover ~ .to235Rc {
  background-color: rgba(75, 110, 132, 1);
}
.countBottom3:hover {
  background-color: rgba(47, 69, 83, 1);
}
.countBottom3:hover ~ .to336 {
  background-color: rgba(254, 110, 134, 1);
}
.countBottom3:hover ~ .to336Rc {
  background-color: rgba(75, 110, 132, 1);
}
.bottomBgc1 {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  position: absolute;
  right: 46.59%;
  top: 0;
  width: 21%;
  height: 92%;
  opacity: 0;
  display: none;
}
.countBottom1:hover ~ .bottomBgc1 {
  opacity: 1;
  display: block;
}
.bottomBgc2 {
  position: absolute;
  right: 23.8%;
  top: 0;
  width: 21%;
  height: 92%;
  opacity: 0;
  display: none;
}
.countBottom2:hover ~ .bottomBgc2 {
  opacity: 1;
  display: block;
}
.bottomBgc3 {
  position: absolute;
  right: 1%;
  top: 0;
  width: 21%;
  height: 92%;
  opacity: 0;
  display: none;
}
.countBottom3:hover ~ .bottomBgc3 {
  opacity: 1;
  display: block;
}
</style>
