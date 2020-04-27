<template>
  <div id="app">
    <div class="question">
      <component
        :is="questions[currentQuestion].component"
        :question="questions[currentQuestion]"
        v-on:next-question="nextQuestion"
      ></component>
    </div>
  </div>
</template>

<script>
import TextComponent from "./components/TextComponent";
import ImageComponent from "./components/ImageComponent";

export default {
  name: "App",
  components: {
    TextComponent,
    ImageComponent
  },
  data() {
    return {
      currentQuestion: 0,
      questions: [
        {
          id: 0,
          component: "TextComponent",
          title: "This is a text question?",
          answers: [
            {
              copy: "answer one",
              goto: 1
            },
            {
              copy: "answer two",
              goto: 2
            }
          ]
        },
        {
          id: 1,
          component: "TextComponent",
          title: "This is question two",
          copy2: "copy2",
          answers: [
            {
              copy: "answer one",
              goto: 2
            },
            {
              copy: "answer two",
              goto: 2
            }
          ]
        },
        {
          id: 2,
          component: "ImageComponent",
          title: "title2",
          copy2: "copy2"
        }
      ]
    };
  },
  methods: {
    nextQuestion(id) {
      this.currentQuestion = id;
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
