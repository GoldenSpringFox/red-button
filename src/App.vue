<template>
  <div class="top">
    <Timer class="center" />
  </div>
  <div class="mid">
    <ButtonPanel class="button-panel center" />
  </div>
</template>

<script>
import ButtonPanel from "./components/ButtonPanel.vue";
import Timer from "./components/Timer";

export default {
  name: "App",
  components: {
    Timer,
    ButtonPanel,
  },
};
</script>

<style>
body {
  margin: 0;
}
#app {
  height: 100vh;
  background: rgb(74, 74, 74);
  display: flex;
  flex-flow: column;
}
.top {
  height: 20vh;
}
.mid {
  height: 80vh;
}
.center {
  margin: 0;
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.button-panel {
  height: 100%;
  width: 100%;
}
</style>
