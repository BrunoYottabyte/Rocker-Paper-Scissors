<template>
  <main>
    <article>
      <h1>YOU PICKED</h1>
      <PaperOptions ref="child" v-if="props.attackSelected == 'paper'" />
      <RockOptions ref="child" v-if="props.attackSelected == 'rock'" />
      <ScissorsOptions ref="child" v-if="props.attackSelected == 'scissors'" />
    </article>
    <div class="placar" v-if="result !== ''">
      <WinOrLose @try-attack="$emit('tryAttack')" :result="result" />
    </div>
    <article>
      <h1>THE HOUSE PICKED</h1>
      <div v-if="!computer" class="placeholder-notselect">
        {{ count }}
      </div>
      <PaperOptions ref="pc" v-if="computer == 'paper'" />
      <RockOptions ref="pc" v-if="computer == 'rock'" />
      <ScissorsOptions ref="pc" v-if="computer == 'scissors'" />
    </article>
  </main>
  <div class="placar-mobile" v-if="result !== ''">
    <WinOrLose @try-attack="$emit('tryAttack')" :result="result" />
  </div>
</template>

<script setup>
import { defineProps, onMounted, ref, nextTick, computed } from "vue";
import PaperOptions from "./PaperOptions.vue";
import RockOptions from "./RockOptions.vue";
import ScissorsOptions from "./ScissorsOptions.vue";
import WinOrLose from "./WinOrLose.vue";
/* eslint-disable */
const props = defineProps({
  attackSelected: String,
  score: Number,
});
const emit = defineEmits(["newScore"]);

const count = ref(5);
const options = ["paper", "scissors", "rock"];
const computer = ref("");

// Jogador
const child = ref(null);

//maquina
const pc = ref(null);

//resultado
const result = ref("");

onMounted(() => {
  console.log(child.value.container);
});
let newS = ref(props.score);
const newScore = computed(() => {
  return newS.value + 1;
});

setTimeout(async () => {
  computer.value = options[Math.floor(Math.random() * 3)];
  // PAPER
  if (props.attackSelected == "paper" && computer.value == "rock") {
    await nextTick();
    child.value?.container.classList.add("win");
    emit("newScore", newScore);
    result.value = "YOU WIN";
  } else if (props.attackSelected == "paper" && computer.value !== "paper") {
    await nextTick();
    pc.value?.container.classList.add("win");
    result.value = "YOU LOSE";
  } else if (props.attackSelected == "paper" && computer.value == "paper") {
    result.value = "DRAW";
  }

  // ROCK
  if (props.attackSelected == "rock" && computer.value == "scissors") {
    await nextTick();
    child.value?.container.classList.add("win");
    emit("newScore", newScore);
    result.value = "YOU WIN";
  } else if (props.attackSelected == "rock" && computer.value !== "rock") {
    await nextTick();
    pc.value?.container.classList.add("win");
    result.value = "YOU LOSE";
  } else if (props.attackSelected == "rock" && computer.value == "rock") {
    result.value = "DRAW";
  }

  // SCISSORS
  if (props.attackSelected == "scissors" && computer.value == "paper") {
    await nextTick();
    child.value?.container.classList.add("win");
    emit("newScore", newScore);
    result.value = "YOU WIN";
  } else if (
    props.attackSelected == "scissors" &&
    computer.value !== "scissors"
  ) {
    await nextTick();
    pc.value?.container.classList.add("win");
    result.value = "YOU LOSE";
  } else if (
    props.attackSelected == "scissors" &&
    computer.value == "scissors"
  ) {
    result.value = "DRAW";
  }
}, Math.floor(Math.random() * 5 + 1) * 1000);

const timer = setInterval(() => {
  if (count.value >= 1 && computer.value == "") {
    count.value--;
  } else {
    clearTimeout(timer);
  }
}, 1000);
</script>

<style scoped>
.placeholder-notselect {
  width: 180px;
  height: 180px;

  background: rgba(0, 0, 0, 0.2);
  border-radius: 100%;

  display: grid;
  place-items: center;
  font-size: 3rem;

  color: rgba(255, 255, 255, 0.4);
}

main {
  display: flex;
  flex-direction: row;
  margin-top: -70px;
  height: max-content;
  justify-content: space-between;
  align-items: center;
}

.placar-mobile {
  display: none;
}

@media (max-width: 768px) {
  .placar {
    display: none;
  }
  main {
    max-width: 90vw;
  }

  .placar-mobile {
    display: block;
    margin-top: -50px;
  }
}

main > article {
  width: 250px;
  height: 250px;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: relative;
}

article h1 {
  letter-spacing: 1.5px;
  margin-bottom: 2.5rem;
  font-size: 0.85rem;
  color: #ffffff;
}

.out-box {
  position: initial;
  pointer-events: none;
}

@media (max-width: 768px) {
  .placeholder-notselect {
    width: 110px;
    height: 110px;
  }

  main > article {
    width: 180px;
    height: 180px;
  }
}
</style>
