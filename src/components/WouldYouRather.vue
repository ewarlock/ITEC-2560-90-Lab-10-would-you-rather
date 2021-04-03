<template>
  <div class="wyr">

    <h2>Please make your choice:</h2>

    <h3>{{ question }}</h3>

    <input type="radio" 
    v-model="choice" 
    v-bind:value="answer1"
    v-on:change="choiceMade">
    <label>{{ answer1 }}</label>

    <input type="radio" 
    v-model="choice" 
    v-bind:value="answer2"
    v-on:change="choiceMade">
    <label>{{ answer2 }}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: { //prop provided by parent, data is for components
  //fill in data types for props
    question: String,
    answer1: String,
    answer2: String
  },
  data() {
    return {
      choice: ""
    }
  },
  methods: {
    choiceMade() {
      //emits an event, good to use a name with a - to avoid JS conflicts
      this.$emit('answer-changed', this.choice)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.wyr {
  border: 10px green solid;
  border-radius: 20px;
  padding: 15px;
  background: darkslategray;
}
</style>
