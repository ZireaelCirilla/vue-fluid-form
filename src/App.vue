<template>
  <div id="app">
    <FluidForm :title="title" :update="false" :inputs="data" @create="create"></FluidForm>
  </div>
</template>

<script>
import FluidForm from "./components/FluidForm";
export default {
  name: "app",
  components: {
    FluidForm
  },
  data() {
    return {
      title: "MyForm",

      user: {
        name: "",
        email: ""
      },

      data: [
        { type: "text", key: "name", name: "Nombre del Gato" },
        { type: "date", key: "date", name: "Fecha de nacimiento" },
        { type: "email", key: "email del usuario", name: "Email del dueño" },
        { type: "password", name: "Contraseña" }
      ]
    };
  },
  methods: {
    create(value) {
      // this.axios
      console.log(value);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
