<script lang="ts" setup>
import FormOptions from "./components/FormOptions.vue";
import FormComposition from "./components/FormComposition.vue";
</script>

<template>
  <!-- <FormOptions /> -->
  <FormComposition />
</template>

<style lang="scss">
* {
  font-family: "Poppins", sans-serif;
}

body {
  background-color: #2ecb70;
}
.root {
  width: 400px;
  margin: 0 auto;
  background-color: #fff;
  padding: 30px;
  margin-top: 100px;
  border-radius: 20px;
}

h2 {
  text-align: center;
}

input {
  border: none;
  outline: none;
  border-bottom: 1px solid #ddd;
  font-weight: 300;
  font-size: 1em;
  padding: 5px 0;
  margin: 10px 0 5px 0;
  width: 100%;
}

button {
  background-color: #3498db;
  padding: 10px 20px;
  margin-top: 10px;
  border: none;
  color: white;
}
</style>
