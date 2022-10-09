<template>
  <article class="container-rules">
    <button @click="viewRules">RULES</button>
  </article>

  <div ref="containerModal" class="container-modal">
    <div class="modal">
      <header>
        <h1>Rules</h1>
        <img
          @click="hiddenRules"
          src="../../doc/images/icon-close.svg"
          alt=""
        />
      </header>
      <img width="300" src="../../doc/images/image-rules.svg" alt="" />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";

const containerModal = ref();

const viewRules = () => {
  containerModal.value.classList.add("active");
};

const hiddenRules = () => {
  containerModal.value.classList.remove("active");
};
</script>

<style>
.container-rules button {
  width: 150px;
  height: 40px;
  border-radius: 6px;

  border: 1px solid #fff;
  display: flex;
  justify-content: center;

  align-items: center;
  letter-spacing: 1px;
  background: transparent;

  color: #ffffff;
  position: absolute;
  bottom: 30px;
  right: 30px;

  cursor: pointer;
  transition: all 0.2s;
}

.container-rules button::before {
  content: "";
  position: absolute;
  width: 0;
  height: 100%;
  top: 0;
  left: 0;

  transition: all 0.4s;
}
.container-rules button:hover {
  color: hsl(229, 64%, 46%);
  outline: 2px solid #ffffff;
  border: 2px solid hsl(229, 66%, 32%);
}
.container-rules button:hover::before {
  content: "";
  background: #ffffff;
  color: hsl(229, 64%, 46%);
  width: 100%;
  z-index: -10;
}

.container-modal {
  width: 100vw;
  height: 100vh;
  position: fixed;

  display: grid;
  place-items: center;
  z-index: 999;

  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);

  transition: all 0.3s;
  pointer-events: none;
  opacity: 0;
}

.container-modal.active {
  pointer-events: initial;
  opacity: 1;
}

.container-modal.active .modal {
  opacity: 1;
  transform: translateY(0vh) scale(1);
}

.modal {
  width: 350px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  background: #ffffff;
  padding: 20px;
  border-radius: 6px;

  transition: all 0.35s cubic-bezier(0.1, 0.2, 0.5, 1.4);

  position: fixed;
  opacity: 0;
  transform: translateY(100vh) scale(0);
}

.modal header h1 {
  margin: 0;
}
.modal header img {
  cursor: pointer;
}
.modal header {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;

  margin-bottom: 2rem;
}

@media (max-width: 768px) {
  .container-rules button {
    position: relative;
    right: 0;
  }

  .modal {
    max-width: 80vw;
  }
}
</style>
