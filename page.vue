<template>
  <timeLine :arr="countArr"></timeLine>
</template>
<script>
import timeLine from "~/components/timeline/index.vue";
export default {
  data() {
    return {
      countArr: [
        {
          name: "邱丽",
          date: "1974.02.06",
          isactive: true
,
status : "在售"        },
        {
          name: "戴平",
          date: "2007.04.21",
          isactive: false,
          status : "在售"
        },
        {
          name: "叶丽",
          date: "2009.12.05",
          isactive: false,
          status : "在售"
        },
        {
          name: "罗超",
          date: "2001.06.23",
          isactive: false,
          status : "在售"
        },
        {
          name: "杜平",
          date: "1976.10.01",
          isactive: false,
          status : "在售"
        },
        {
          name: "沈秀英",
          date: "2018.10.05",
          isactive: false,
          status : "在售"
        },
        {
          name: "汤强",
          date: "1976.12.20",
          isactive: false,
          status : "在售"
        }
      ]
    };
  },
  components: {
    timeLine
  }
};
</script>
<style>
</style>