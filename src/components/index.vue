<template>
  <span>{{ textNumber }}</span>
</template>
<script lang="ts">
// https://blog.csdn.net/sushauai/article/details/52958162
// https://github.com/PanJiaChen/vue-countTo
// https://juejin.cn/post/6844903709189603335
// https://segmentfault.com/a/1190000021737705
// http://panjiachen.github.io/countTo/demo/
// https://github.com/newcaoguo/EasyRollingNumber
// https://github.com/Chef5/jQuery.rollNumber
// https://juejin.cn/post/7041700222111596580
import { defineComponent, ref, toRefs } from "vue";

export default defineComponent({
  props: {
    startVal: {
      type: Number,
      default: 0,
      required: true,
    },
    endVal: {
      type: Number,
      default: 0,
      required: false,
    },
    duration: {
      type: Number,
      default: 3000,
      required: false,
    },
    decimals: {
      type: Number,
      default: 0,
      required: false,
      validator(value: number) {
        return value >= 0;
      },
    },
  },
  setup(props) {
    const separator = ",";
    const duration = 3000;
    const { startVal } = toRefs(props);

    let textNumber: string = ref("");

    // let timer = null as any;

    const addLabel = (value: number): string => {
      return value.toString().replace(/(\d)(?=(?:\d{3})+$)/g, "$1,");
    };
    let total = 0;
    let timer = setInterval(() => {
      console.log(addLabel(startVal.value));
      textNumber.value = addLabel(100000000);
      total++;
      if (total === duration) {
        clearInterval(timer);
      }
    }, 1000);
    return {
      textNumber,
    };
  },
});
</script>
