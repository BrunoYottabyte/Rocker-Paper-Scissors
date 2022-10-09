<template>
  <div class="container">
    <div class="triangle"></div>
    <PaperOptions @click="$emit('selectAttack', 'paper')" />
    <RockOptions @click="$emit('selectAttack', 'rock')" />
    <ScissorsOptions @click="$emit('selectAttack', 'scissors')" />
  </div>
</template>

<script setup>
import PaperOptions from "./PaperOptions.vue";
import RockOptions from "./RockOptions.vue";
import ScissorsOptions from "./ScissorsOptions.vue";
</script>

<style>
.container {
  height: 280px;
  width: 280px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.triangle {
  height: 280px;
  width: 280px;

  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  clip-path: polygon(50% 100%, 100% 15%, 0% 15%);
  background-color: rgba(0, 0, 0, 0.2);
}

.triangle::before {
  content: "";
  width: 80%;
  height: 85%;
  clip-path: polygon(50% 100%, 100% 15%, 0% 15%);
  position: absolute;
  z-index: -1;
  background: radial-gradient(
    ellipse at top,
    hsla(212, 44%, 29%, 0.507) 0%,
    hsl(237, 48%, 17%) 60%
  );
}

.out-box {
  width: 180px;
  height: 180px;
  border-radius: 100%;

  display: flex;
  justify-content: center;
  align-items: center;

  box-shadow: inset 0px -9px 0px hsl(230, 62%, 45%),
    0px 10px 8px rgba(0, 0, 0, 0.4);
  z-index: 999;
  position: absolute;

  cursor: pointer;
  user-select: none;
  transition: all 0.2s;
}

.out-box:active {
  box-shadow: inset 0px -3px 0px hsl(230, 66%, 36%);
}

.out-box:active .box {
  box-shadow: inset -2px 3px 3px rgba(0, 0, 0, 0.4),
    inset -2px 3px 25px rgba(0, 0, 0, 0.4);
}

.out-box .shadow,
.out-box .shadow-two,
.out-box .shadow-three {
  position: absolute;
  width: 100%;
  height: 100%;

  border-radius: 100%;
  background-color: #ffffff;
  opacity: 0;
  z-index: -5;
}

.out-box.win .shadow {
  animation: pulse 2.9s ease-out infinite;
}

.out-box.win .shadow-two {
  animation: pulse 2.9s 0.8s ease-out infinite;
}
.out-box.win .shadow-three {
  animation: pulse 2.9s 1.4s ease-out infinite;
}

@keyframes pulse {
  0% {
    opacity: 0.15;
  }
  100% {
    transform: scale(2);
    opacity: 0;
  }
}

.out-box-1 {
  background: linear-gradient(hsl(230, 89%, 62%), hsl(230, 89%, 65%));
  top: -50px;
  left: -100px;
}

.out-box-2 {
  background: linear-gradient(hsl(349, 71%, 52%), hsl(349, 70%, 56%));
  box-shadow: inset 0px -9px 0px hsl(349, 68%, 38%),
    0px 10px 8px rgba(0, 0, 0, 0.4);
  bottom: -50px;
}

.out-box-2:active {
  box-shadow: inset 0px -3px 0px hsl(349, 71%, 34%);
}

.out-box-3 {
  background: linear-gradient(hsl(39, 89%, 49%), hsl(40, 84%, 53%));
  box-shadow: inset 0px -9px 0px hsl(39, 87%, 38%),
    0px 10px 8px rgba(0, 0, 0, 0.4);

  top: -50px;
  right: -100px;
}

.out-box-3:active {
  box-shadow: inset 0px -3px 0px hsl(39, 84%, 36%);
}

.box {
  width: 140px;
  height: 140px;
  border-radius: 100%;

  background-color: #ffffff;
  box-shadow: inset -2px 7px 3px rgba(0, 0, 0, 0.25);
  transition: all 0.2s;

  display: flex;
  justify-content: center;
  align-content: center;
}

.box img {
  margin: auto;
  width: 70px;
  height: 80px;
}

@media (max-width: 768px) {
  body {
    background: linear-gradient(
      hsl(214, 44%, 29%),
      hsl(237, 49%, 15%) 85%
    ) !important;
  }
  .container {
    width: 70vw;
    height: 150px;
  }

  .triangle {
    height: 200px;
    width: 200px;
  }

  .triangle::before {
    background: linear-gradient(hsl(213, 47%, 26%), hsl(237, 49%, 15%));
    width: 80%;
  }

  .out-box {
    width: 110px;
    height: 110px;
  }

  .out-box-1 {
    top: -50px;
    left: -25px;
    box-shadow: inset 0px -5px 0px hsl(230, 62%, 45%);
  }
  .out-box-2 {
    box-shadow: inset 0px -5px 0px hsl(349, 68%, 38%);
  }
  .out-box-3 {
    background: linear-gradient(hsl(39, 89%, 49%), hsl(40, 84%, 53%));
    box-shadow: inset 0px -5px 0px hsl(39, 87%, 38%);

    top: -50px;
    right: -25px;
  }

  .box {
    width: 80px;
    height: 80px;
    box-shadow: inset -2px 4px 3px rgba(0, 0, 0, 0.25);
  }

  .box img {
    width: 35px;
    height: 45px;
  }
}
</style>
