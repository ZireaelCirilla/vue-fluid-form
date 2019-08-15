<template>
  <div class="fluid-input">
    <p v-if="inputInstructions.name">{{inputInstructions.name}}:</p>
    <input
      :type="type"
      v-model="inputInstructions.value"
      :class="inputInstructions.type"
      :list="inputInstructions.type == 'email' ? 'domains': ''"
    />
    <div v-if="inputInstructions.type == 'password'" id="togglePassword-container">
      <button
        @click="type=='password' ? type = 'text': type = 'password'"
        id="togglePassword"
      >{{this.type=='password' ? 'Show': 'Hide'}}</button>
    </div>
    <div v-if="inputInstructions.type == 'email'">
      <datalist id="domains">
        <option
          v-if="!inputInstructions.value.includes(this.gmail)"
          :value="inputInstructions.value + this.gmail"
        ></option>
        <option
          v-if="!inputInstructions.value.includes(this.hotmail)"
          :value="inputInstructions.value+ this.hotmail"
        ></option>
        <option
          v-if="!inputInstructions.value.includes(this.yahoo)"
          :value="inputInstructions.value+ this.yahoo"
        ></option>
      </datalist>
    </div>
  </div>
</template>

<script>
export default {
  name: "FluidInput",
  props: ["inputInstructions"],
  data() {
    return {
      gmail: "@gmail.com",
      hotmail: "@hotmail.com",
      yahoo: "@yahoo.com"
    };
  },
  created: function() {},
  computed: {
    type() {
      return this.inputInstructions.type;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input {
  padding: 5px;
  flex-basis: 90%;
  border: 0;
  background-color: rgba(170, 170, 170, 0);
  outline: 0;
}
p {
  margin: 0;
  margin-right: 5px;
}
.fluid-input {
  display: flex;
  flex-wrap: wrap;
  border-style: solid;
  border-width: 1.5px;
  border-radius: 5px;
  border-color: gray;
  background-color: rgba(170, 170, 170, 0.123);
}
.text {
}
.date {
}
.password {
}
.email {
}
#togglePassword {
  background-color: rgba(170, 170, 170, 0.301);
  border: 0;
  height: 100%;
  width: 100%;
  border-radius: 5px;
  outline: 0;
  transition: 250ms;
}
#togglePassword:active {
  transform: scale(1.05);
}

#togglePassword-container {
  flex-basis: 9%;
}
</style>
