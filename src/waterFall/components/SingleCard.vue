<template>
  <div class="card">
    <slot name="content"></slot>
  </div>
</template>

<script>
export default {
  name: "SingleCard",
};
</script>

<style scoped>
img {
  width: 100%;
}
</style>
