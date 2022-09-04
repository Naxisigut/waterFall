<template>
  <div class="container" ref="container">
    <SingleCol v-for="(col, idx) in colDataList" :key="idx">
      <SingleCard v-for="(item, index) in col" :key="index">
        <!-- 插槽透传 -->
        <template #content>
          <slot name="content" :item="item"></slot>
        </template>
      </SingleCard>
    </SingleCol>
  </div>
</template>

<script>
import SingleCard from "./components/SingleCard.vue";
import SingleCol from "./components/SingleCol.vue";
export default {
  name: "WaterFall",
  components: { SingleCard, SingleCol },
  props: {
    /* 接收的数据 */
    list: {
      type: Array,
      default: () => [],
    },
    /* 约定列数 */
    col: {
      type: Number,
      default: 3,
    },
  },
  data() {
    return {
      /* 当前渲染索引 */
      renderIndex: -1,

      /* 当前所有列的数据，数组包数组的形式 */
      /* index从小到大依次对应页面从左往右的列 */
      colDataList: Array.from(new Array(this.col), () => []),

      /* 当前所有列的节点数组, 在组件mounted时获取 */
      colNodeList: null,
    };
  },
  watch: {
    list: {
      immediate: true,
      deep: true,
      handler() {
        // 每次list更新，将渲染索引改为未更新的首个元素的索引
        this.$nextTick(() => this.renderIndex++);
      },
    },

    /* 每当渲染索引变化，渲染单张瀑布流卡片 */
    /* 每次渲染完毕，索引值会停在当前list的length-1 */
    renderIndex(idx, oldIdx) {
      if (oldIdx === undefined || !this.list) return;

      let index = this.getMinIndex(this.colNodeList); // 获得最短列的索引
      this.colDataList[index].push(this.list[idx]); // 将data push到最短列里面
    },
  },
  methods: {
    /* 获得最短列的索引号 */
    getMinIndex(HtmlArr) {
      const arr = HtmlArr.map((item) => item.offsetHeight);
      let val = Math.min(...arr);
      return arr.findIndex((item) => item === val);
    },
  },
  mounted() {
    this.colNodeList = Array.from(this.$refs.container.children);
  },
  updated() {
    //一次渲染一条数据，增加索引，直到最大索引
    // 思考是否有一次渲染所有卡片的方法？
    // 好像没有，因为节点的高度只有在渲染完成后才能获取
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
</style>
