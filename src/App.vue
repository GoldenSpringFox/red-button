<template>
  <Timer class="timer" />
  <ButtonPanel />
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
.timer {
  flex: 0 0 auto;
  margin: 20px auto;
}
</style>
