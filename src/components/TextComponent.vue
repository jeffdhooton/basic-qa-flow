<template>
  <div>
    <h2>{{ question.title }}</h2>
    <!--
      Iterate over every answer inside the question prop,
      set a key on the button (needed in Vue), attach a
      click listener with @click and inside the click listener,
      emit an event called `next-question` with the data of the
      answer's goto ID.
     -->
    <button
      v-for="response in question.answers"
      :key="response.copy"
      @click="$emit('next-question', response.goto)"
    >
      <!--
        Using {{ var_name }} you can render data straight from props,
        computed methods, or the data property of the component straight
        to the dom
      -->
      {{ response.copy }}
    </button>
  </div>
</template>

<script>
export default {
  name: "TextComponent",
  /**
   * Have to declare props that are coming into the component,
   * if we were using typescript, we could type these out so that
   * there is no chance of having a runtime TypeError. Not necessary tho
   */
  props: ["question" /**: Object */]
};
</script>

<style lang="scss" scoped>
/*
  Can scope all styling to this specific component by adding the scoped attr onto the style tag
 */
</style>
