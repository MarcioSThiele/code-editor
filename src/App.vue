<template>
  <MyComponent />
</template>

<script>
import MyComponent from "./components/MyComponent.vue";

export default {
  name: "App",
  components: { MyComponent },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  font-size: x-large;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
