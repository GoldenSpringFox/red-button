<template>
  <div class="red-btn" @click="increaseCounter">
    <p class="big counter">{{ this.counter }}</p>
    <p class="small counter">{{ this.counter }}</p>
  </div>
</template>

<script>
export default {
  name: "RedButton",
  data() {
    return {
      counter: 0,
    };
  },
  methods: {
    increaseCounter() {
      this.counter = this.counter + 1;
    },
  },
};
</script>

<style>
.red-btn {
  background: rgb(226, 26, 26);
  border-radius: 50%;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 1), 0 0 0 6px grey;
  text-align: center;
  position: relative;
  box-sizing: border-box;

  /* flexbox */
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.red-btn:hover {
  cursor: pointer;
}
.red-btn:active {
  background: rgb(200, 26, 26);
  box-shadow: 0 0 0 6px grey;
}

.counter {
  color: white;
  font: bold;
  font-family: "Copperplate", fantasy;
  display: block;
  margin: 0;

  /* make unselectable */
  user-select: none;
  -moz-user-select: none;
  -khtml-user-select: none;
  -webkit-user-select: none;
  -o-user-select: none;
}
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
