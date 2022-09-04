<template>
  <div id="app">
    <WaterFall :list="list" :col="5">
      <template #content="{ item }">
        <!-- <div>{{ item }}</div> -->
        <img :src="item" alt="" />
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
      // list: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12],
      list: [
        "https://img1.baidu.com/it/u=1966616150,2146512490&fm=253&fmt=auto&app=138&f=JPEG?w=751&h=500",
        "https://img1.baidu.com/it/u=2204132179,643663242&fm=253&fmt=auto&app=120&f=JPEG?w=1200&h=800",
        "https://img1.baidu.com/it/u=2218815005,3124653454&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
        "https://img0.baidu.com/it/u=1278618774,2401043221&fm=253&fmt=auto&app=138&f=JPEG?w=575&h=500",
        "https://img1.baidu.com/it/u=3384796346,381674655&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
        "https://img2.baidu.com/it/u=3908142881,2459234098&fm=253&fmt=auto&app=138&f=JPEG?w=750&h=500",
        "https://img1.baidu.com/it/u=1546227440,2897989905&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
        "https://img2.baidu.com/it/u=3638146059,2337065608&fm=253&fmt=auto&app=120&f=JPEG?w=812&h=500",
        "https://img1.baidu.com/it/u=3672431567,2990196533&fm=253&fmt=auto&app=138&f=JPEG?w=667&h=500",
        "https://img2.baidu.com/it/u=2048195462,703560066&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=333",
        "https://img1.baidu.com/it/u=3164998783,2199444470&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=333",
        "https://img2.baidu.com/it/u=515536710,1509093089&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
        "https://img1.baidu.com/it/u=2658939207,2791674017&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
        "https://img1.baidu.com/it/u=745998857,124348167&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=281",
        "https://img1.baidu.com/it/u=842625417,583290252&fm=253&fmt=auto&app=138&f=JPEG?w=808&h=500",
      ],
    };
  },
  methods: {
    click() {
      // const count = Math.ceil(Math.random() * 20);
      // const arr = Array.from(new Array(count), () => Math.random() * 10);
      // this.list.push(...arr);
      this.list.push(...this.list);
    },
  },
};
</script>

<style>
#app {
  width: 500px;
}
</style>
