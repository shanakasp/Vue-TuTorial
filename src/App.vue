<template>
  <div id="app">
    <p>Welcome {{ message }}</p>
    <p v-if="num === 0">Ha Ha Ha</p>
    <p v-else-if="num > 0">Number is positive</p>
    <p v-else>Number is not zero</p>

    <!-- HTML content rendered (still unsafe in real apps) -->
    <p v-html="safeHack"></p>

    <!-- Disabled button -->
    <button :disabled="isDisabled">Bind Button</button>

    <!-- Conditionally shown element -->
    <div v-show="showElement">
      <p>Hello world</p>
    </div>

    <!-- Loops -->
    <div class="for">
      <p v-for="name in names" :key="name"></p>

      <h3 v-for="(name, index) in fullNames" :key="name.firstName">
        {{ index }} {{ name.firstName }} {{ name.lastName }}
      </h3>

      <h2>Add Method - {{ add(10, 20, 30) }}</h2>
      <h2>Multiply Method - {{ multiply(10) }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      names: ["Brusce", "Clark", "Diana"],
      fullNames: [
        { firstName: "Bruce", lastName: "Wayne" },
        { firstName: "Clark", lastName: "Kent" },
        { firstName: "Diana", lastName: "Prince" },
      ],
      message: "Hello Vue!",
      greet: "Greet you!",
      num: 10,
      safeHack: `<a href="#" onclick="alert('Hey You!')">Click me</a>`,
      isDisabled: false,
      showElement: true,
      baseValue: 20,
    };
  },
  methods: {
    alertUser() {
      alert("You are alerted");
    },
    add(a, b, c) {
      return a + b + c;
    },
    multiply(num) {
      return num * this.baseValue;
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
