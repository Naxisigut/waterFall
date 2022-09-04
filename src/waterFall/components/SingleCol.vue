<template>
  <div class="columnBox">
    <!-- 默认插槽 -->
    <slot></slot>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.columnBox {
  flex: 1;
  margin: 0 10px;
  display: flex;
  justify-content: start;
  flex-direction: column;
}
</style>
