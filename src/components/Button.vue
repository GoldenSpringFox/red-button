<template>
  <div class="btn" :style="{ background: color }">
    <p class="text primary">{{ this.primaryText }}</p>
    <p class="text secondary">{{ this.secondaryText }}</p>
  </div>
</template>

<script>
export default {
  name: "Button",
  props: {
    color: String,
    clickedColor: String,
    primaryText: String,
    secondaryText: String,
  },
};
</script>

<style scoped>
.btn {
  border-radius: 50%;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 1), 0 0 0 6px grey;
  position: relative;

  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.red-btn:hover {
  cursor: pointer;
}
.text {
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
.text.primary {
  font-size: 17vmin;
  margin-top: 30px;
}
.text.secondary {
  font-size: 24px;
  width: 200px;
  height: 50px;
}
</style>
