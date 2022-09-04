<template>
  <div class="card">
    <slot name="content"></slot>
  </div>
</template>

<script>
export default {
  props: {
    contents: {
      type: String,
      default: "test",
    },
  },
};
</script>

<style></style>
