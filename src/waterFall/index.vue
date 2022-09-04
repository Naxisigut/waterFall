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
      //每当接收到新数据，把渲染序号重置为0
      immediate: true,
      handler() {
        this.$nextTick(() => (this.renderIndex = 0));
      },
    },
    /* 渲染单张瀑布流卡片 */
    renderIndex: {
      immediate: true,
      handler(idx, oldIdx) {
        if (oldIdx === undefined) return;
        if (!this.list) return;
        if (this.renderIndex >= this.list.length) return; // 此时渲染完毕
        // 获得最短的列的索引
        let index = this.getMinIndex(Array.from(this.$refs.container.children));
        this.colList[index].push(this.list[idx]); // 将data push到最短的列里面
      },
    },
  },
  methods: {
    /* 获得最短的列的索引号 */
    getMinIndex(HtmlArr) {
      const arr = HtmlArr.map((item) => item.clientHeight);
      let val = Math.min(...arr);
      return arr.findIndex((item) => item == val);
    },
  },
  updated() {
    //一次渲染一条数据，增加索引，直到最大索引
    // 思考是否有一次渲染所有卡片的方法？
    console.log("updated =");
    if (this.renderIndex < this.list.length) this.renderIndex++;
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  align-items: flex-start;
}
.columnBox {
  /* width: 33%; */
  flex: 1;
  margin: 0 10px;
  /* min-height: 200px; */
  background-color: red;
}
.el-button:focus,
.el-button:hover {
  color: #606266;
  border-color: #dcdfe6;
  background-color: #eee;
}
</style>
