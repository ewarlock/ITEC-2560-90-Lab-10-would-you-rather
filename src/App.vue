<template>
  <div id="app">
    <!--template can only have one child - use div-->
    <h1>Would You Rather?</h1>

    <!--include components by referencing them in here, by name-->
    <!--converts uppercase into format with dashes, useful-->
    <!--but using dash format is optional... but vue prefers it to differentiate from HTML-->
    <would-you-rather v-for="question in questions"
    v-bind:key="question.id"
    v-bind:question="question"
    v-on:answer-changed="answerChanged"
    ></would-you-rather>

    <!--only shows up once user has started answering questions-->
    <div id="answers" v-if="answers.length > 0">
      <h1>You Would Rather</h1>

      <!--display the user's choice in li for each choice in answers-->
      <ul v-for:="answer in answers">
        <li>{{ answer.choice }}</li>
      </ul>
    </div>

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
      //all the questions for component
      questions: [
        {
          id: 0,
          prompt: "Would you rather have a magic carpet that flies or a see-through submarine?",
          answer1: "Have A Magic Carpet",
          answer2: "Have A See-Through Submarine"
        },
        {
          id: 1,
          prompt: "Would you rather only be able to walk on all fours or only be able to walk sideways like a crab?",
          answer1: "Walk On All Fours",
          answer2: "Walk Sideways Like A Crab"
        },
        {
          id: 2,
          prompt: "Would you rather live in a base under the ocean or a floating base in the sky?",
          answer1: "Have A Base Under the Ocean",
          answer2: "Have A Base Floating in the Sky"
        },
      ],
      //answers to be filled when user makes selections
      answers: [],
    }
  },
  methods: {
    answerChanged(answerUser) {
      //only pushes answerUser object to answers if ID is unique
      let counter = 0
      this.answers.forEach(answer => {
        if (answerUser.id === answer.id)
          counter++
      })
      if (counter === 0)
        this.answers.push(answerUser)
    }
  }
}
</script>

<style>
body {
  background: seagreen;
  color: white;
}
li {
  text-align: left;
  font-size: larger;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}
#answers {
  background: darkslategray;
  border: 10px dotted green;
  border-radius: 20px;
  margin-left: 20%;
  margin-right: 20%;
}
</style>
