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

      <h2>{{ count }}</h2>

      <button @click="increment(5)">Increment by 5</button>
      <button v-on:click="increment(10)">Increment by 10</button>
      <button v-on:click="decrement">Decrement</button>

      <h1>Forms</h1>
      <form>
        <label for="name">Name</label>
        <input type="text" id="name" v-model="formValues.name" />
        <select v-model="formValues.country">
          <option value="">Select any country</option>
          <option value="Sri Lanka">Sri Lanka</option>
          <option value="Singapore">Singapore</option>
        </select>

        <label for="remote">Able to work remote</label>
        <input type="checkbox" id="remote" v-model="formValues.remote" />
        <pre
          >{{ formValues.name }}  {{ formValues.country }} {{
            formValues.remote
          }}</pre
        >
      </form>
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
      count: 0,

      formValues: {
        name: "",
        country: "",
        remote: "",
      },
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
    increment(num) {
      this.count += num;
    },
    decrement() {
      this.count -= 1;
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
