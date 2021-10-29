<template>
  <div ref="button" class="button" :style="styles">
    <div class="text">
      <div class="primary">{{ this.primaryText }}</div>
      <div class="secondary">{{ this.secondaryText }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Button",
  props: {
    color: String,
    textColor: String,
    primaryText: String,
    secondaryText: String,
  },
  computed: {
    styles() {
      return {
        "--button-size": this.buttonSize + "px",
        "--background-color": this.color,
        "--text-color": this.textColor,
      };
    },
  },
  data() {
    return {
      buttonSize: null,
    };
  },
  mounted() {
    window.addEventListener("resize", this.myEventHandler);
    this.myEventHandler();
  },
  unmounted() {
    window.removeEventListener("resize", this.myEventHandler);
  },
  methods: {
    myEventHandler() {
      this.buttonSize = Math.min(
        this.$refs.button.offsetWidth,
        this.$refs.button.offsetHeight
      );
    },
  },
};
</script>

<style scoped>
.button {
  background: var(--background-color, darkgrey);
  border-radius: 50%;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 1), 0 0 0 6px grey;
  position: relative;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.button:hover {
  cursor: pointer;
}
.button:active {
  box-shadow: 0 0 0 6px grey;
}
.text {
  color: var(--text-color);
  font: bold;
  font-family: "Copperplate", fantasy;
  margin: 0;

  display: flex;
  flex-direction: column;

  /* make unselectable */
  user-select: none;
  -moz-user-select: none;
  -khtml-user-select: none;
  -webkit-user-select: none;
  -o-user-select: none;
}
.primary {
  font-size: calc(var(--button-size) / 3);
}
.secondary {
  font-size: calc(var(--button-size) / 10);
}
</style>
