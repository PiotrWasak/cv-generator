<template>
  <div id="app">
    <CVForm />
  </div>
</template>

<script>
import CVForm from "./components/CVForm.vue";

export default {
  name: "App",
  components: {
    CVForm,
  },
};
</script>

<style scoped>
#app {
  background: url(assets/background.png) no-repeat center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  font-family: "Lato";
  height: 100vh;
  margin-top: 0;
  padding-top: 4em;
}
i {
  font-size: 2em;
  color: rgb(84, 36, 185);
}
</style>
