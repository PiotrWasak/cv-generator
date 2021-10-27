<template>
  <CVForm />
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

<style>
body {
  background: url(assets/background.png) no-repeat center center fixed;
  -webkit-background-size: cover;
  -moz-background-size: cover;
  -o-background-size: cover;
  background-size: cover;
  font-family: "Lato";
}
i {
  font-size: 2em;
  color: rgb(84, 36, 185);
}
</style>
