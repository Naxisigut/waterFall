<template>
  <div class="container" ref="container">
    <div class="columnBox" v-for="(col, idx) in colList" :key="idx">
      <SingleCard v-for="(item, index) in col" :key="index">
        <!-- 插槽透传 -->
        <template #content>
          <slot name="content" :item="item"></slot>
        </template>
      </SingleCard>
    </div>
  </div>
</template>

<script>
import SingleCard from "./components/SingleCard.vue";
export default {
  name: "WaterFall",
  components: { SingleCard },
  props: {
    list: {
      type: Array,
      default: () => [],
    },
    col: {
      type: Number,
      default: 3,
    },
  },
  data() {
    return {
      renderIndex: -1,
      colList: Array.from(new Array(this.col), () => []),
    };
  },
  watch: {
    list: {
      immediate: true,
      deep: true,
      handler() {
        // if (oldVal) return; // 只有第一次渲染时需要从0开始
        this.$nextTick(() => this.renderIndex++);
      },
    },

    /* 渲染单张瀑布流卡片 */
    renderIndex(idx, oldIdx) {
      if (oldIdx === undefined || !this.list) return;
      if (this.renderIndex >= this.list.length) return; // 此时渲染完毕
      let index = this.getMinIndex(Array.from(this.$refs.container.children)); // 获得最短列的索引
      this.colList[index].push(this.list[idx]); // 将data push到最短的列里面
    },
  },
  methods: {
    /* 获得最短列的索引号 */
    getMinIndex(HtmlArr) {
      const arr = HtmlArr.map((item) => item.offsetHeight);
      let val = Math.min(...arr);
      return arr.findIndex((item) => item == val);
    },
  },
  updated() {
    //一次渲染一条数据，增加索引，直到最大索引
    // 思考是否有一次渲染所有卡片的方法？
    // 好像没有，节点的高度只有在渲染完成后才能获取
    if (this.renderIndex < this.list.length - 1) this.renderIndex++;
  },
};
</script>

<style scoped>
.container {
  width: 100%;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: flex-start;
}
.columnBox {
  flex: 1;
  margin: 0 10px;
  background-color: red;
}
</style>
