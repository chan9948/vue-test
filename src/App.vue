<template>
  <AnimedBar/>
  <ColorPicker/>
  <LoadingBar :progessValue="value"/>
  <button @click="changeValue(0)">0</button>
  <button @click="changeValue(100)">100</button>
  <Chart :value="value"/>
</template>

<script>
import LoadingBar from './components/LoadingBar.vue'
import Chart from './components/Chart.vue';
import ColorPicker from './components/ColorPicker.vue';
import AnimedBar from './components/AnimedBar.vue';

export default {
  name: 'App',
  components: {
    LoadingBar,
    Chart,
    ColorPicker,
    AnimedBar
  },
  data() {
    return {
      value : 0,
    }
  },methods: {
    changeValue: function (newValue) {
      this.value = newValue;
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
