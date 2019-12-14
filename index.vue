<template>
  <div class="timeLine">
    <div class="time_top">
      <div
        v-for="(item , index) in obj.arr"
        :key="index"
        :class="{padding : index + 1 !==1 , content : true ,defaultContent : !item.isactive }"
      >
        <div class="info">
          <p>{{item.date}}</p>
          <p>{{item.status}}</p>
        </div>
        <div class="trigon"></div>
      </div>
    </div>
    <div class="border clearFix">
      <div
        :class="!item.isactive ? 'defaultBorderContent' : 'border_content'"
        v-for="(item , index) in obj.countArr"
        :key="index"
      >
        <div class="circle"></div>
        <div class="line"></div>
      </div>
    </div>
    <div class="time_top bottom">
      <div
        v-for="(item , index) in obj.arr2"
        :key="index"
        :class="!item.isactive ? 'content padding defaultContent' : 'content padding' "
      >
        <div class="info">
          <p>{{item.date}}</p>
          <p>{{item.status}}</p>
        </div>
        <div class="trigon trigon_bottom"></div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "timeLine",
  props: {
    "arr" : Array
  },
  data() {
    return {
      obj: {
        //奇数
        arr: [],
        //偶数
        arr2: [],
        //总的数量
        countArr: []
      }
    };
  },
  methods: {
    //判断是奇数还是偶数
    isEvenOrOddNumber(num) {
      if (num === 0) {
        return true;
      }
      if (num % 2 == 0) {
        return true;
      } else {
        return false;
      }
    },
    splitArr(arr) {
      let is = !arr.length ;
      if(is) {
        throw new Error("请正确传值")
      }else {
       arr.forEach((item, index)=>{
         this.obj.countArr.push(item);
         let isEvenOrOdd = this.isEvenOrOddNumber(index + 1)
         isEvenOrOdd ? this.obj.arr2.push(item) : this.obj.arr.push(item)
       })
      }
    }
  },
  created() {
    this.splitArr(this.arr)
   
  },
};
</script>
<style lang="scss" scoped>
.timeLine {
  width: 710px;
  height: 175px;
  margin: 0 auto;

  .time_top {
    height: 66px;
    .content {
      width: 100px;
      height: 100%;
      background-color: #f1f8ff;
      position: relative;
      display: inline-block;

      .info {
        height: 44px;
        text-align: center;
        color: #2d8cf0;
        font-size: 16px;
      }
      .trigon {
        width: 0;
        height: 0;
        border: 10px solid #f1f8ff;
        border-left-color: transparent;
        border-bottom-color: transparent;
        border-right-color: transparent;
        position: absolute;
        top: 100%;
        left: 50%;
        margin-left: -10px;
      }
      .trigon_bottom {
        top: -20px;
        transform: rotate(-180deg);
      }
    }
    .defaultContent {
      @extend .content;
      background-color: #f7f7f7;

      .info {
        height: 44px;
        text-align: center;
        color: #999;
        font-size: 16px;
      }
      .trigon {
        width: 0;
        height: 0;
        border: 10px solid #f7f7f7;
        border-left-color: transparent;
        border-bottom-color: transparent;
        border-right-color: transparent;
        position: absolute;
        top: 100%;
        left: 50%;
        margin-left: -10px;
      }
    }
  }
  .border {
    width: 100%;
    height: 24px;
    margin: 7px 0;

    .border_content {
      width: 100px;
      height: 100%;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      float: left;
      .circle {
        width: 17px;
        height: 17px;
        border: 4.15px solid #2d8cf0;
        border-radius: 50%;
        position: absolute;
      }
      .line {
        width: 100%;
        height: 2px;
        background-color: #2d8cf0;
        position: absolute;
        left: 50%;
        top: 70%;
      }
    }
    .defaultBorderContent {
      @extend .border_content;
      .circle {
        width: 17px;
        height: 17px;
        border: 4.15px solid #ddd;
        border-radius: 50%;
        position: absolute;
      }
      .line {
        width: 100%;
        border: 2px dashed #ddd;
        background-color: transparent;
        position: absolute;
        left: 50%;
        top: 70%;
      }
    }
    div:last-child {
      .line {
        display: none;
      }
    }
  }
}
.bottom {
  width: 100%;
  justify-content: space-around !important;
}
.padding {
  margin-left: 100px;
}
</style>