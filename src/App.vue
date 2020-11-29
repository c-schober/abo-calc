<template>
  <div id="app">
    <RangeSlider @intervalRange="intervalRange" />
    <WashSlider @calcWash="calcWash"/>
    <SpuelSlider @calcSpuel="calcSpuel"/>
    <DataObject :number-wash="wash" :number-spuel="spuel" :range="range" ></DataObject>

  </div>
</template>

<script>

import RangeSlider from "@/components/RangeSlider";
import DataObject from "@/components/DataObject";
import WashSlider from "@/components/WashSlider";
import SpuelSlider from "@/components/SpuelSlider";
export default {
  name: 'App',
  components: {
    SpuelSlider,
    WashSlider,
    DataObject,
    RangeSlider
  },
  data() {
    return {
      range: [],
      wash: 0,
      spuel: 0
    }
  },
  methods: {
    intervalRange(range){
      this.range = range;
    },
    calcWash(val){
      this.wash = val;
    },
    calcSpuel(val){
      this.spuel = val;
    }
  }
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

.slider {
  width: 400px;
  margin: 0 auto;
  display:block;
}
</style>
