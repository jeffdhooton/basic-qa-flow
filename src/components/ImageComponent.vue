<template>
  <div>
    <!--
      This is just a dumb component to show the difference
      between rendering different types of components dynamically.
    -->
    <h2>Image Card</h2>
  </div>
</template>

<script>
export default {
  name: "ImageComponent",
  props: ["question" /**: Object */]
};
</script>

<style lang="scss" scoped></style>
