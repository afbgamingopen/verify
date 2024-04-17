<script setup>
import Overview from "./components/overview.vue";
import Implementation from "./components/implementation.vue";
import Calculation from "./components/calculation.vue";
import { parseQuery } from "vue-router";
import { ref } from "vue";

let query = parseQuery(location.search);
let activeName = ref("overview");
if (query["game"] != undefined && query["game"] != "") {
  activeName = ref("calculation");
}

function isiOS() {
  return (
    /iPad|iPhone|iPod/.test(navigator.userAgent) ||
    (navigator.platform === "MacIntel" && navigator.maxTouchPoints > 1)
  );
}
const isIOS = isiOS();
// 使用示例
//阻止safari浏览器双击放大功能
let lastTouchEnd = 0; //更新手指弹起的时间
document.documentElement.addEventListener("touchstart", function (event) {
  //多根手指同时按下屏幕，禁止默认行为
  if (event.touches.length > 1) {
    event.preventDefault();
  }
});
document.documentElement.addEventListener(
  "touchend",
  function (event) {
    let now = new Date().getTime();
    if (now - lastTouchEnd <= 300) {
      //当两次手指弹起的时间小于300毫秒，认为双击屏幕行为
      event.preventDefault();
    } else {
      // 否则重新手指弹起的时间
      lastTouchEnd = now;
    }
  },
  false
);
let paramsAllTime = 0;
document.documentElement.addEventListener(
  "click",
  function (event) {
    let now = new Date().getTime();
    if (paramsAllTime == 0) {
      //自定义事件、组件传值，排除掉
      return;
    }
    if (now - paramsAllTime <= 300) {
      //当两次手指弹起的时间小于300毫秒，认为双击屏幕行为
      event.preventDefault();
    } else {
      // 否则重新手指弹起的时间
      paramsAllTime = now;
    }
  },
  false
);
//阻止双指放大页面
document.documentElement.addEventListener("gesturestart", function (event) {
  event.preventDefault();
});
</script>

<template>
  <div class="common-layout" :class="isIOS ? 'isIos' : ''">
    <el-container>
      <el-header>Provably Fair</el-header>
      <el-main>
        <el-tabs v-model="activeName" class="tabs">
          <el-tab-pane label="Overview" name="overview">
            <Overview />
          </el-tab-pane>
          <el-tab-pane label="Implementation" name="implementation">
            <Implementation />
          </el-tab-pane>
          <el-tab-pane label="Calculation" name="calculation">
            <Calculation />
          </el-tab-pane>
        </el-tabs>
      </el-main>
      <el-footer>
        Get source
        <a href="https://github.com/afbgamingopen/verify" target="_blank"
          >Github.com</a
        >
      </el-footer>
    </el-container>
    <div class="commonYd" v-if="isIOS"></div>
  </div>
</template>
<style scoped>
header {
  line-height: 60px;
  font-size: 50px;
}

.common-layout {
  max-width: 1280px;
  width: 100%;
  height: 100%;
  font-weight: normal;
  margin: 0 auto;
}
.isIos {
  height: 100vh;
  overflow: hidden;
  overflow-y: scroll;
}
.isIos::-webkit-scrollbar {
  width: 0;
}

.commonYd {
  height: 80px;
  width: 100%;
}
</style>
