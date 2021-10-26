<template>
  <div class="button-panel">
    <div ref="redBtnContainer" class="button-container">
      <RedButton
        ref="redBtn"
        class="red-button"
        :style="{
          width: this.redButtonDiameter + 'px',
          height: this.redButtonDiameter + 'px',
        }"
      />
    </div>
    <!-- <YellowButton /> -->
  </div>
</template>

<script>
import RedButton from "./RedButton.vue";

export default {
  name: "ButtonPanel",
  components: {
    RedButton,
  },
  data() {
    return {
      redButtonDiameter: null,
    };
  },
  mounted() {
    return this.minDivLength("redBtnContainer");
  },
  methods: {
    minDivLength(containerRef) {
      this.redButtonDiameter = Math.min(
        this.$refs[containerRef].offsetHeight,
        this.$refs[containerRef].offsetWidth
      );
    },
  },
};
</script>

<style>
.button-panel {
  flex: 1 1 auto;
  overflow: hidden;
  display: grid;
  grid-template-columns: 20% 60% 20%;
  grid-template-rows: 15% 60% 25%;
  grid-template-areas:
    "top top top"
    "left main right"
    "bot bot bot";
  /* gap: 10px 10px; */
  place-items: stretch;
  place-content: center;
}
.button-container {
  grid-area: main;
}
.red-button {
  position: relative;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
</style>
