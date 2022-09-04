<template>
  <div id="app">
    <WaterFall :list="list" :col="5">
      <template #content="{ item }">
        <div class="myCard">
          <a href="javascript:;">
            <img :src="item" alt="" />
            <div class="context">
              <div class="title">title</div>
              <div class="detail">detail....</div>
            </div>
          </a>
        </div>
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
        "https://img2.baidu.com/it/u=1483173994,3145449881&fm=253&fmt=auto&app=138&f=JPEG?w=231&h=500",
        "https://img1.baidu.com/it/u=2218815005,3124653454&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
        "https://img0.baidu.com/it/u=1278618774,2401043221&fm=253&fmt=auto&app=138&f=JPEG?w=575&h=500",
        "https://img0.baidu.com/it/u=3502695619,2304702653&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=889",
        "https://img2.baidu.com/it/u=3908142881,2459234098&fm=253&fmt=auto&app=138&f=JPEG?w=750&h=500",
        "https://img1.baidu.com/it/u=1546227440,2897989905&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
        "https://img2.baidu.com/it/u=2710439350,3824130137&fm=253&fmt=auto&app=138&f=JPEG?w=281&h=500",
        "https://img1.baidu.com/it/u=3672431567,2990196533&fm=253&fmt=auto&app=138&f=JPEG?w=667&h=500",
        "https://img0.baidu.com/it/u=117050405,72083886&fm=253&fmt=auto&app=138&f=JPEG?w=231&h=500",
        "https://img1.baidu.com/it/u=3164998783,2199444470&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=333",
        "https://img1.baidu.com/it/u=482122514,1271319416&fm=253&fmt=auto&app=138&f=JPEG?w=400&h=711",
        "https://img1.baidu.com/it/u=2658939207,2791674017&fm=253&fmt=auto&app=138&f=JPEG?w=889&h=500",
        "https://img1.baidu.com/it/u=745998857,124348167&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=281",
        "https://img1.baidu.com/it/u=842625417,583290252&fm=253&fmt=auto&app=138&f=JPEG?w=808&h=500",
        "https://img2.baidu.com/it/u=3467919694,3192607261&fm=253&fmt=auto&app=138&f=JPEG?w=400&h=710",
        "https://img1.baidu.com/it/u=3570234568,2447872064&fm=253&fmt=auto&app=138&f=JPEG?w=231&h=500",
        "https://img1.baidu.com/it/u=150224905,2949440557&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=1082",
        "https://img2.baidu.com/it/u=3232620659,37260345&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=888",
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
  width: 1024px;
  margin: 0 auto;
}
.myCard {
  border-radius: 10px;
  background-color: #f6f6f6;
  overflow: hidden;
  box-shadow: 7px 7px 12px rgba(0, 0, 0, 0.4),
    -7px -7px 12px rgba(255, 255, 255, 0.9);
}
.myCard img {
  width: 100%;
}
.context {
  padding: 20px;
  padding-top: 10px;
}
.title {
  font-size: 20px;
  margin-bottom: 5px;
}
.detail {
  /* padding-left: 10px; */
}
a {
  color: #333;
  text-decoration: none;
}
</style>
