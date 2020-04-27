<template>
  <div>
    <h2>{{ question.title }}</h2>
    <button
      v-for="response in question.answers"
      :key="response.copy"
      @click="$emit('next-question', response.goto)"
    >
      {{ response.copy }}
    </button>
  </div>
</template>

<script>
export default {
  name: "TextComponent",
  props: ["question"],
  mounted() {
    console.log("mounted");
  }
};
</script>

<style lang="scss" scoped></style>
