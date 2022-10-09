<template>
  <main ref="containerResult">
    <h1 class="result">{{ result }}</h1>
    <button class="try" @click="$emit('tryAttack')">PLAY AGAIN</button>
  </main>
</template>

<script setup>
/* eslint-disable */

import { defineProps, onMounted, onUpdated, ref, watch } from "vue";
const containerResult = ref(null);
const props = defineProps({
  result: String,
});

onMounted(() => {
  if (props.result == "YOU WIN") {
    console.log(containerResult);
    containerResult.value.classList.remove("lose");
    containerResult.value.classList.add("win");
  }
  if (props.result == "YOU LOSE") {
    containerResult.value.classList.remove("win");
    containerResult.value.classList.add("lose");
  }
});
</script>

<style scoped>
main {
  display: flex;
  flex-direction: column !important;
  justify-content: center;
  margin-top: 70px !important;
}
.result {
  font-size: 3.2rem;
  letter-spacing: 1px;
  margin: 0;
  margin-bottom: 0.5rem;
  color: #ffffff;
}

.try {
  width: 150px;
  height: 35px;
  border-radius: 6px;

  border: none;

  display: grid;
  place-items: center;
  background: #ffffff;

  transition: all 0.3s;
  cursor: pointer;
}
.try:hover {
  background: hsl(228, 1%, 35%);
  color: #ffffff;
}

.win .try {
  color: hsl(229, 64%, 46%);
}

.lose .try {
  color: hsl(349, 70%, 56%);
}

.win .try:hover {
  background: hsl(229, 64%, 46%);
  color: #ffffff;
}

.lose .try:hover {
  background: hsl(349, 70%, 56%);
  color: #ffffff;
}

@media (max-width: 768px) {
  .try {
    width: 200px;
    height: 40px;
  }
}
</style>
