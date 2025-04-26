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
      <form @submit="submit">
        <label for="name">Name</label>
        <input type="text" id="name" v-model="formValues.name" />
        <select v-model="formValues.country">
          <option value="">Select any country</option>
          <option value="Sri Lanka">Sri Lanka</option>
          <option value="Singapore">Singapore</option>
        </select>

        <label for="remote">Able to work remote</label>
        <input type="checkbox" id="remote" v-model="formValues.remote" />

        <label for="yearsOfExpreiince"
          >How many years of experience you got?</label
        >
        <label id="3-5">3-5 years of expreince</label>
        <input
          type="radio"
          id="3-5"
          value="3-5"
          v-model="formValues.yearsOfExpereince"
        />
        <label id="5-10">5-10 years of expreince</label>
        <input
          type="radio"
          id="5-10"
          value="5-10"
          v-model="formValues.yearsOfExpereince"
        />
        <label id="10+">10+ years of expreince</label>
        <input type="radiobutton" />
        <pre
          >{{ formValues.name }}  {{ formValues.country }} {{
            formValues.remote
          }} {{ formValues.yearsOfExpereince }}</pre
        >
        <div><button>Submit</button></div>
      </form>
    </div>

    <div><h2>Volume controller</h2></div>

    <button @click="increaseVolume">Increment</button>
    <button @click="decreaseVolume">Decrement</button>

    <h2>Volume is {{ volume }}</h2>

    <h2>Imported Components</h2>
    <TryThis msg="Hello" secondMsg="Bye Bye" />
  </div>
</template>

<script>
import TryThis from "./components/TryThis.vue";

export default {
  name: "App",
  components: {
    TryThis,
  },
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
      volume: 0,

      formValues: {
        name: "",
        country: "",
        remote: "",
        yearsOfExpereince: "",
      },
    };
  },
  watch: {
    volume(newVal, oldVal) {
      if (newVal > oldVal && newVal === 10) {
        alert("Volume is at max");
      }
    },
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

    submit(event) {
      event.preventDefault();
      console.log("Form Submitted");
      console.log("Form values,", this.formValues);
    },
    increaseVolume() {
      this.volume += 1;
    },

    decreaseVolume() {
      this.volume -= 1;
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
