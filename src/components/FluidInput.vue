<template>
  <div class="fluid-input">
    <p v-if="inputInstructions.name">{{inputInstructions.name}}:</p>
    <input
      :type="type"
      v-model="value"
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
        <option v-if="!this.value.includes(this.gmail)" :value="this.value + this.gmail"></option>
        <option v-if="!this.value.includes(this.hotmail)" :value="this.value+ this.hotmail"></option>
        <option v-if="!this.value.includes(this.yahoo)" :value="this.value+ this.yahoo"></option>
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
      value: this.inputInstructions.value,
      type: this.inputInstructions.type,
      gmail: "@gmail.com",
      hotmail: "@hotmail.com",
      yahoo: "@yahoo.com"
    };
  },
  created: function() {},
  computed: {},
  watch: {
    value: function(val) {
      this.value = val;
      this.inputInstructions.value = val;
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
  font-size: 14px;
  padding: 5px;
  flex-basis: 100%;
}
.fluid-input {
  display: flex;
  flex-wrap: wrap;
  border-style: solid;
  border-width: 1.5px;
  border-radius: 5px;
  border-color: gray;
  background-color: rgba(170, 170, 170, 0.123);
  text-align: left;
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
  height: 80%;
  width: 95%;
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
