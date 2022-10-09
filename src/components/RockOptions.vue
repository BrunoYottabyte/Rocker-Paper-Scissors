<template>
  <div ref="container" class="out-box out-box-2">
    <div class="shadow"></div>
    <div class="shadow-two"></div>
    <div class="shadow-three"></div>
    <div class="box">
      <img
        draggable="false"
        src="../../doc/images/icon-rock.svg"
        alt="icon rock"
      />
    </div>
  </div>
</template>
<script setup>
import { ref, defineExpose } from "vue";

const container = ref();

defineExpose({
  container,
});
</script>
