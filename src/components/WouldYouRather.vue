<template>
  <div class="wyr">

    <h2>Please make your choice:</h2>

    <h3>{{ question.prompt }}</h3>

    <input type="radio" 
    v-model="answerUser.choice" 
    v-bind:value="question.answer1"
    v-on:change="choiceMade">
    <label>{{ question.answer1 }}</label>

    <input type="radio" 
    v-model="answerUser.choice" 
    v-bind:value="question.answer2"
    v-on:change="choiceMade">
    <label>{{ question.answer2 }}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  props: { //prop provided by parent, data is for components
  //fill in data types for props
    question: Object,
  },
  data() {
    return { //make unique "answer" object with same ID as originating question
      answerUser: {
        id: this.question.id,
        choice: ""
      }
    }
  },
  methods: {
    choiceMade() {
      //emits an event, good to use a name with a - to avoid JS conflicts
      //sends the answerUser object... I feel like this runs into the same problem
      //that we ran into for student sign in where the component is altering App.vue's data thru v-model?
      //am unsure?
      this.$emit('answer-changed', this.answerUser)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 10px;
}
.wyr {
  border: 5px green solid;
  border-radius: 20px;
  padding: 20px;
  margin: 20px;
  background: darkslategray;
}
</style>
