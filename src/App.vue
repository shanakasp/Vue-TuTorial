<template>
  <div id="app">
    <p>Welcome {{ message }}</p>
    <p v-if="num === 0">Ha Ha Ha</p>
    <p v-else-if="num > 0">Number is positive</p>
    <p v-else>Number is not zero</p>
    <p v-html="safeHack"></p>
    <button v-bind:disabled="isDisabled">Bind Button</button>
  </div>

  <div v-show="showElement">
    <p>Hello world</p>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      message: "Hello Vue!",
      greet: "Greet you!",
      num: 10,
      safeHack: `<a href="#" onclick="alert("Hey You!")>Click me</a>`,
      isDisabled: false,
      showElement: true,
    };
  },
  methods: {
    alertUser() {
      alert("You are alerted");
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
