<template>
  <div class="bar">
    <div
      v-for="(item, index) in items"
      :key="index"
      :style="{
        overflow: 'hidden',
        width: 0,
        backgroundColor: '#' + item.color,
        height: '100%',
        flexGrow: item.width,
        transition: 'flex-grow 1s ease, background-color 1s ease',
      }"
      class="cell"
    >
      <transition>
        <div v-if="item.width > 10" :style="{ color: '#' + getTextColor(item.color) }">
          {{ item.text }}
        </div>
      </transition>
    </div>
  </div>
  <button @click="change">change</button>
</template>
<script>
export default {
  name: "AnimedBar",
  data() {
    return {
      items: [
        {
          width: 1,
          color: "123456",
          text: "hi",
        },
        {
          width: 1,
          color: "ddd213",
          text: "hisda",
        },
        {
          width: 1,
          color: "14d123",
          text: "hidsad asda",
        },
        {
          width: 1,
          color: "612372",
          text: "hi 213",
        },
        {
          width: 1,
          color: "923213",
          text: "hi dsa 1230",
        },
        {
          width: 1,
          color: "f31232",
          text: "hi yo you",
        },
      ],
    };
  },
  mounted() {
    this.change();
  },
  methods: {
    change: function () {
      let tmpItems = this.items;
      let targetInex = Math.floor(Math.random() * tmpItems.length);
      tmpItems.forEach((item, index) => {
        if (index == targetInex) {
          item.width = 100;
        } else {
          item.width = Math.floor(Math.random() * 10) + 1;
        }
        item.color = Math.floor(Math.random() * 16777215).toString(16);
      });
      this.items = tmpItems;
    },
    getTextColor: function (bgColor) {
      let r = parseInt(bgColor.slice(0, 2), 16);
      let g = parseInt(bgColor.slice(2, 4), 16);
      let b = parseInt(bgColor.slice(4, 6), 16);

      if (r + g + b > (3 * 256) / 2) {
        return "000000";
      } else {
        return "FFFFFF";
      }
    },
    // getTextColor: function (bgColor) {
    //   let r = (255 - parseInt(bgColor.slice(0, 2), 16)).toString(16);
    //   let g = (255 - parseInt(bgColor.slice(2, 4), 16)).toString(16);
    //   let b = (255 - parseInt(bgColor.slice(4, 6), 16)).toString(16);

    //   let color = this.padZero(r) + this.padZero(g) + this.padZero(b);
    //   console.log(color);
    //   return color;
    // },
    // padZero: function (str, len) {
    //   len = len || 2;
    //   var zeros = new Array(len).join("0");
    //   return (zeros + str).slice(-len);
    // },
  },
};
</script>
<style>
.bar {
  width: 100%;
  height: 100px;
  background-color: black;
  display: flex;
}
.cell {
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  overflow: hidden;
  white-space: nowrap;
}
.v-enter-active,
.v-leave-active {
  transition: opacity 1s;
}
.v-enter-from,
.v-leave-to {
  opacity: 0;
}
.v-enter-to,
.v-leave-from {
  opacity: 1;
}
</style>
