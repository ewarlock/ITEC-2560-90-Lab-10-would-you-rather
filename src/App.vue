<template>
  <div id="app">
    <!--template can only have one child - use div-->
    <h1>Would You Rather?</h1>

    <!--include components by referencing them in here, by name-->
    <!--converts uppercase into format with dashes, useful-->
    <!--but using dash format is optional... but vue prefers it to differentiate from HTML-->
    <would-you-rather 
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged"
    ></would-you-rather>

    <h3>{{ userSelectionMessage }}</h3>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: "Would you rather have a magic carpet that flies or a see-through submarine?",
      wyrAnswer1: "Magic Carpet",
      wyrAnswer2: "See-Through Submarine",
      userSelectionMessage: ""
    }
  },
  methods: {
    answerChanged(choice) {
      this.userSelectionMessage = `Thanks! You chose ${choice}`
    }
  }
}
</script>

<style>
body {
  background: seagreen;
  color: white;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
</style>
