<template>
  <main>
    <div class="box-score-options">
      <ScoreComponent :score="score" />
      <OptionsAttack v-if="!attackSelected" @select-attack="handleAttack" />
      <OptionsSelected
        @new-score="handleNewScore"
        :score="score"
        v-else
        :attack-selected="typeAttack"
        @try-attack="handleTry"
      />
    </div>
    <RulesComponent />
  </main>
</template>

<script setup>
import ScoreComponent from "./components/ScoreComponent.vue";
import OptionsAttack from "./components/OptionsAttack.vue";
import RulesComponent from "./components/RulesComponent.vue";
import OptionsSelected from "./components/OptionsSelected.vue";

import { ref } from "vue";
const score = ref(0);
const attackSelected = ref(false);
const typeAttack = ref(null);

const handleAttack = (value) => {
  attackSelected.value = true;
  typeAttack.value = value;
};

const handleTry = () => {
  attackSelected.value = false;
};

const handleNewScore = (value) => {
  score.value = value;
};
</script>

<style>
* {
  font-family: "Barlow Semi Condensed", sans-serif;
  user-select: none;
}

body {
  padding: 0px;
  margin: 0px;
  width: 100vw;

  min-height: 100vh;

  overflow: hidden;

  display: flex;
  justify-content: center;
  align-items: center;

  background: radial-gradient(
    ellipse at top,
    hsl(214, 44%, 29%) 2%,
    hsl(237, 49%, 15%) 50%
  );
  background-size: cover;
}

main {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;

  height: 90vh;
}

.box-score-options {
  display: flex;
  flex-direction: column;
  align-items: center;
}

@media (max-width: 768px) {
  main {
    height: 95vh;
  }
}
</style>
