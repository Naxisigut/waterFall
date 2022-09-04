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
.card {
  margin-bottom: 20px;
}
img {
  width: 100%;
}
</style>
