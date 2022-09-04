<template>
  <div id="app">
    <WaterFall :list="list" :col="7">
      <template #content="{ item }">
        <div>{{ item }}</div>
      </template>
    </WaterFall>
    <button @click="click">增加数据</button>
  </div>
</template>

<script>
import WaterFall from "./waterFall/index.vue";
export default {
  name: "App",
  components: { WaterFall },
  data() {
    return {
      list: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13],
    };
  },
  methods: {
    click() {
      const count = Math.ceil(Math.random() * 20);
      const arr = Array.from(new Array(count), () => Math.random() * 10);
      this.list.push(...arr);
    },
  },
};
</script>

<style></style>
