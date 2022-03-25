<template>
  <view>
    <ui-clunch ref="clunch" height="400px"></ui-clunch>
  </view>
</template>

<script>
import uiClunch from "clunch/platform/uni-app/index.vue";
import radar from "@clunch/radar";
export default {
  mounted() {
    let clunch = this.$refs.clunch.new(
      {
        animation: false,

        // 温馨提示：这里的val1和val2是需要在clunch的data中定义的，进行了双向绑定
        // 如果后续改变了，比如val1变了，直接： clunch.val1= 新的值  即可
        template: `<ui-radar :indicator="val1" :data="val2"/>`,
        methods: {
          doit(target) {
            console.log(target);
          },
        },
        data() {
          return {
            val1: [
              { name: "销售（Sales）", max: 6500 },
              { name: "管理（Administration）", max: 16000 },
              { name: "信息技术（Information Technology）", max: 30000 },
              { name: "客服（Customer Support）", max: 38000 },
              { name: "研发（Development）", max: 52000 },
              { name: "市场（Marketing）", max: 25000 },
            ],
            val2: [
              {
                value: [4200, 3000, 20000, 35000, 50000, 18000],
                name: "预算分配（Allocated Budget）",
              },
              {
                value: [5000, 14000, 28000, 26000, 42000, 21000],
                name: "实际开销（Actual Spending）",
              },
            ],
          };
        },
      },
      {
        "ui-radar": radar,
      }
    );
    console.log(clunch);
  },
  components: {
    uiClunch,
  },
};
</script>

<style>
</style>
