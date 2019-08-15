<template>
  <div class="fluid-form">
    <p class="title">{{title}}</p>
    <div v-for="input in inputs">
      <FluidInput :inputInstructions="input" class="FluidInput"></FluidInput>
    </div>
    <div class="footer">
      <button>Cancel</button>
      <button
        @click="$emit(update ? 'update' : 'create', sendValues())"
      >{{update ? 'Update' : 'Create'}}</button>
    </div>
  </div>
</template>

<script>
import FluidInput from "./FluidInput";
export default {
  name: "FluidForm",
  props: ["title", "update", "inputs"],
  components: {
    FluidInput
  },
  data() {
    return {};
  },
  methods: {
    sendValues() {
      var obj = {};
      this.inputs.forEach(input => {
        if (input.key) {
          obj[input.key] = input.value;
        }
      });
      return obj;
    }
  },
  created() {
    this.inputs.forEach(element => {
      element.value = "";
    });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title {
  text-align: left;
}
.fluid-form {
  border: gray;
  border-style: solid;
  border-width: 1.5px;
  border-radius: 5px;
  border-color: gray;
  padding: 5px;
}
.FluidInput {
  margin: 0.5%;
}
.footer {
  display: flex;
  justify-content: flex-end;
}
button {
  background-color: rgba(170, 170, 170, 0.301);
  border: 0;
  height: 100%;
  border-radius: 5px;
  outline: 0;
  transition: 250ms;
  width: 10%;
  height: 25px;
  margin: 5px;
}
button:active {
  transform: scale(1.05);
}
</style>
