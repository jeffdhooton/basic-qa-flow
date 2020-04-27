<template>
  <div id="app">
    <div class="question">
      <!--
        :is sets the specific component that is going to be rendered
        dynamically.

        :question passes along the current question to the specific component
        responsible for rendering

        v-on:next-question catches 'next-question' event emitted from specific components
        and binds that event to the nextQuestion method in the methods property on this
        App.vue component
      -->
      <component
        :is="questions[currentQuestion].component"
        :question="questions[currentQuestion]"
        v-on:next-question="nextQuestion"
      ></component>
    </div>
  </div>
</template>

<script>
/**
 * Import all of the components that can be rendered through this App.vue component.
 */
import TextComponent from "./components/TextComponent";
import ImageComponent from "./components/ImageComponent";

export default {
  name: "App",
  components: {
    /**
     * A list of components that you want to make available to the template of this
     * component
     */
    TextComponent,
    ImageComponent
  },
  data() {
    return {
      currentQuestion: 0 /** Track current question index */,
      questions: [
        {
          id: 0 /** First question should always have ID of 0 to match array index  */,
          component:
            "TextComponent" /** Should match the name of the component imported into this file */,
          title: "This is a text question?",
          answers: [
            /**
             * Array of answers, each with a target ID when clicked, can even
             * attach a function as a property on each of these answers to fire
             * off specific Analytics tracking events when it enters the nextQuestion
             * function.
             *
             */
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
      /**
       * We will handle all analytics tracking inside this function, or a similar
       * function to handle the last question in an engagement.
       *
       * The other responsibility of this function is to set the currentQuestion index.
       */
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
