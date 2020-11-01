<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  <Joke />
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import Joke from "./components/Joke.vue";

export default {
  name: "App",
  components: {
    Joke
  }
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Itim&display=swap');
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  font-family: 'Itim', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
  /* margin-top: 60px; */
}

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
</style>
