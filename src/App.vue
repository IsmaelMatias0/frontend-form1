<template>
  <div id="app">
    <RegisterForm />
  </div>
</template>

<script>
import RegisterForm from "./components/RegisterForm.vue";

export default {
  name: "App",
  components: {
    RegisterForm
  }
};
</script>

<style>
/* Esto aplica a toda la página */
html, body, #app {
  height: 100%;
  margin: 0;
  padding: 0;
  background-color: #ffffff; /* fondo blanco total */
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: Arial, sans-serif;
  color: #1e3a8a; /* color de texto por defecto */
}
</style>