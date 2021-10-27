<template>
  <Button
    class="red-button"
    :="redButton"
    @click="clicked"
    @mousedown="heldDown"
    @mouseup="released"
  />
</template>

<script>
import Button from "./Button.vue";

export default {
  name: "RedButton",
  components: {
    Button,
  },
  data() {
    return {
      counter: 0,
      redButton: {
        color: "rgb(225, 25, 25)",
        primaryText: "0",
        secondaryText: "0",
      },
    };
  },
  watch: {
    counter() {
      this.redButton.primaryText = this.counterFormattedWithLetters();
      this.redButton.secondaryText = this.counterFormattedWithCommas();
    },
  },
  methods: {
    clicked() {
      this.counter = this.counter + 1;
    },
    heldDown() {
      this.redButton.color = "rgb(200, 25, 25)";
    },
    released() {
      this.redButton.color = "rgb(225, 25, 25)";
    },
    counterFormattedWithCommas() {
      return this.counter.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
    },
    counterFormattedWithLetters() {
      const lookup = [
        { value: 1, symbol: "" },
        { value: 1e3, symbol: "k" },
        { value: 1e6, symbol: "M" },
        { value: 1e9, symbol: "B" },
        { value: 1e12, symbol: "Tr" },
        { value: 1e15, symbol: "Quad" },
        { value: 1e18, symbol: "Quin" },
      ];
      const rx = /\.0+$|(\.[0-9]*[1-9])0+$/;
      let item = lookup
        .slice()
        .reverse()
        .find((num) => {
          return this.counter >= num.value;
        });
      return item
        ? (this.counter / item.value).toFixed(1).replace(rx, "$1") + item.symbol
        : "0";
    },
  },
};
</script>

<style>
.counter.big {
  font-size: 17vmin;
  margin-top: 30px;
}
.counter.small {
  font-size: 24px;
  width: 200px;
  height: 50px;
}
</style>
