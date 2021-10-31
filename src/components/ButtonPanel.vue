<template>
  <div class="button-panel">
    <div ref="mainBtnContainer" class="main-button-container">
      <RedButton ref="redBtn" class="red-button" />
    </div>
    <!-- <YellowButton /> -->
  </div>
</template>

<script>
import RedButton from "./button_types/RedButton.vue";

export default {
  name: "ButtonPanel",
  components: {
    RedButton,
  },
};
</script>

<style>
.button-panel {
  overflow: hidden;
  display: grid;
  grid-template-columns: 1fr var(--main-button-size) 1fr;
  grid-template-rows: 1fr var(--main-button-size) 2fr;
  grid-template-areas:
    "top top top"
    "left main right"
    "bot bot bot";
  /* gap: 10px 10px; */
  place-items: stretch;
  place-content: center;
}
.main-button-container {
  grid-area: main;
}
.red-button {
  position: relative;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 100%;
  height: 100%;
}
</style>
