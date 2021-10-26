<template>
  <div class="timer-box" @click="this.toggleTimer()">
    <p class="timer-text">{{ this.formattedTime }}</p>
  </div>
</template>

<script>
export default {
  name: "Timer",
  data() {
    return {
      time: 0,
      stoptime: false,
      timer: null,
    };
  },
  computed: {
    formattedTime() {
      return `
        ${("00" + (Math.floor(this.time / 100 / 60 / 60) % 24)).slice(-2)} :
        ${("00" + (Math.floor(this.time / 100 / 60) % 60)).slice(-2)} :
        ${("00" + (Math.floor(this.time / 100) % 60)).slice(-2)} .
        ${("00" + (this.time % 100)).slice(-2)}`;
    },
  },
  methods: {
    toggleTimer() {
      this.stoptime = !this.stoptime;
      if (!this.stoptime) {
        this.timer = setInterval(() => this.time++, 10);
      } else {
        clearInterval(this.timer);
      }
    },
  },
};
</script>

<style>
.timer-box {
  background: rgb(40, 40, 40);
  height: 50px;
  width: 400px;
  box-shadow: inset 5px 5px 8px rgba(0, 0, 0, 0.5);

  display: flex;
  flex-direction: column;
  justify-content: center;
}
.timer-text {
  color: white;
  font-family: "Digital-7 Mono", "Lucida Console", Arial, sans-serif;
  display: block;
  margin: 0 auto;
  font-size: 40px;
  font-variant-numeric: lining-nums tabular-nums;

  /* make unselectable */
  user-select: none;
  -moz-user-select: none;
  -khtml-user-select: none;
  -webkit-user-select: none;
  -o-user-select: none;
}
</style>
