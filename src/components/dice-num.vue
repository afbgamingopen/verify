<script setup>

</script>

<template>
  <div class="wrap svelte-16rlbb1">
    <div class="numcontent svelte-16rlbb1" style="left: 0%;">
      <div class="value svelte-16rlbb1">0</div>
    </div>
    <div class="numcontent svelte-16rlbb1" style="left: 25%;">
      <div class="value svelte-16rlbb1">25</div>
    </div>
    <div class="numcontent svelte-16rlbb1" style="left: 50%;">
      <div class="value svelte-16rlbb1">50</div>
    </div>
    <div class="numcontent svelte-16rlbb1" style="left: 75%;">
      <div class="value svelte-16rlbb1">75</div>
    </div>
    <div class="numcontent svelte-16rlbb1" style="left: 100%;">
      <div class="value svelte-16rlbb1">100</div>
    </div>
  </div>
</template>

<style scoped>
.wrap.svelte-16rlbb1 {
  position: absolute;
  bottom: calc(100% - 1px);
  left: calc(1.5em + 4px);
  right: calc(1.5em + 4px)
}

.numcontent.svelte-16rlbb1 {
  position: absolute;
  text-align: center;
  transform: translate(-50%)
}

.numcontent.svelte-16rlbb1:after {
  content: "";
  bottom: 0;
  position: absolute;
  transform: translate(-50%);
  width: 0;
  height: 0;
  border-left: 6px solid transparent;
  border-right: 6px solid transparent;
  border-bottom: 6px solid var(--grey-400)
}

.value.svelte-16rlbb1 {
  position: absolute;
  font-weight: 600;
  left: 50%;
  bottom: 0;
  transform: translate(-50%,-50%)
}

</style>
