<template>
  <div id="app">
    <WaterFall :list="[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]" :col="7">
      <template #content="{ item }">
        <div>{{ item }}</div>
      </template>
    </WaterFall>
  </div>
</template>

<script>
import WaterFall from "./waterFall/index.vue";
export default {
  name: "App",
  components: { WaterFall },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
