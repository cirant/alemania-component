<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App"></HelloWorld>
    <Buttom @add="mainClick">hola</Buttom>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Buttom from "./components/ButtonComponent.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
    Buttom
  },
  methods: {
    mainClick() {
      console.log("este es un main click");
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
