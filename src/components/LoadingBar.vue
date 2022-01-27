<template lang="">
  <div class="back">
    <div class="num">{{value}}%</div>
    <div class="bar" :style="{width: getPercentage}"></div>
  </div>
</template>
<script>
export default {
  name: "LoadingBar",
  props: {
    progessValue: Number,
  },
  data() {
      return {
          value:0,
      }
  },
  mounted() {
    // console.log(this.progessValue);
  },
  computed: {
    getPercentage: function (){
        return this.value + "%";
    },
  },
  updated() {
      if(this.value < this.progessValue) {
          setTimeout(() => {
              this.value++;
          }, 5);
      }
      if(this.value > this.progessValue) {
          setTimeout(() => {
              this.value--;
          }, 5);
      }
  },
};
</script>
<style scoped>
.back {
  width: 100%;
  height: 15px;
  background-color: #eee;
  border-radius: 10px;
  border: 1px solid #363;
}
.bar {
  width: 100%;
  height: 100%;
  background-color: #8F8;
  border-radius: 10px;
}
.num{
  position: absolute;
  width:100%;
}
</style>
