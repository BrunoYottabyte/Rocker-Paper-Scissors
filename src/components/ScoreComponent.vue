<template>
  <article class="container-score">
    <h1>
      ROCK <br />
      PAPER <br />
      SCISSORS
    </h1>

    <div class="score">
      <p>SCORE</p>
      <h2>{{ props.score }}</h2>
    </div>
  </article>
</template>

<script setup>
/* eslint-disable */
import { defineProps } from "vue";
const props = defineProps({
  score: Number,
});
</script>

<style scoped>
.container-score h1,
.container-score h2 {
  margin: 0px;
}

.container-score h1 {
  font-weight: bold;
  font-size: 1.9rem;
  color: #ffffff;

  line-height: 24px;
}
.container-score {
  margin-bottom: 130px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 20px;
  width: 50vw;
  height: 80px;

  border: 3px solid hsl(217, 16%, 45%);
  border-radius: 10px;
}
.score {
  width: 120px;
  height: 100%;
  background: #ffffff;

  display: flex;
  flex-direction: column;
  align-items: center;

  justify-content: center;
  border-radius: 6px;
}
.score p {
  margin: 0;
  margin-bottom: -5px;
  font-size: 0.85rem;

  letter-spacing: 1px;
  color: hsl(229, 64%, 46%);
}
.score h2 {
  margin: 0;
  font-size: 3rem;
  color: hsl(217, 16%, 45%);
}

@media (max-width: 768px) {
  .container-score {
    margin-bottom: 150px;
    width: 70vw;
    height: 70px;
    padding: 15px;
  }
  .container-score h1 {
    font-size: 1.3rem;
    line-height: 18px;
  }

  .score {
    width: 80px;
  }
  .score p {
    font-size: 0.8rem;
    font-weight: bold;
  }
  .score h2 {
    font-size: 2.5rem;
  }
}

@media (max-width: 400px) {
  .container-score {
    margin-bottom: 100px;
  }
}
</style>
