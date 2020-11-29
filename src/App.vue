<template>
  <div id="app">
      <RangeSlider @intervalRange="intervalRange"/>
    <div class="columns is-multiline is-centered">
      <div class="column is-narrow">
        <WashSlider @calcWash="calcWash"/>
        <SpuelSlider @calcSpuel="calcSpuel"/>
        <Overdelivery @calcLimit="calcLimit"/>
      </div>
      <div class="column is-narrow">
        <PriceLimit @calcPriceEndpoints="calcPriceEndpoints"/>
        <PriceWash @calcPriceWash="calcPriceWash"/>
        <PriceSpuel @calcPriceSpuel="calcPriceSpuel"/>
      </div>
    </div>

    <div class="info">
      <p>Waschmittel Basis ist 19 in vollen Schritten! => 1 Pack Waschmittel = 19 WL // 3 Pack Waschmittel = 57 WL
        usw...</p>
      <p>Spültabs Basis ist 20 in 0,5er Schritten! => 1 Pack Spülmittel = 20 Tabs // 4,5 Pack Spülmittel = 90 Tabs
        usw...</p>
    </div>

    <DataObject :limit="limit" :number-spuel="spuel" :number-wash="wash" :price-endpoints="priceEndpoints"
                :price-spuel="priceSpuel" :price-wash="priceWash"
                :range="range"></DataObject>


  </div>
</template>

<script>

import RangeSlider from "@/components/RangeSlider";
import DataObject from "@/components/DataObject";
import WashSlider from "@/components/WashSlider";
import SpuelSlider from "@/components/SpuelSlider";
import Overdelivery from "@/components/Overdelivery";
import PriceLimit from "@/components/PriceLimit";
import PriceWash from "@/components/PriceWash";
import PriceSpuel from "@/components/PriceSpuel";

export default {
  name: 'App',
  components: {
    PriceSpuel,
    PriceWash,
    PriceLimit,
    Overdelivery,
    SpuelSlider,
    WashSlider,
    DataObject,
    RangeSlider
  },
  data() {
    return {
      range: [],
      wash: 0,
      spuel: 0,
      limit: 0,
      priceEndpoints: [],
      priceWash: 0,
      priceSpuel: 0
    }
  },
  methods: {
    intervalRange(val) {
      this.range = val;
    },
    calcWash(val) {
      this.wash = val;
    },
    calcSpuel(val) {
      this.spuel = val;
    },
    calcLimit(val) {
      this.limit = val;
    },
    calcPriceEndpoints(val) {
      this.priceEndpoints = val;
    },
    calcPriceWash(val) {
      this.priceWash = val;
    },
    calcPriceSpuel(val) {
      this.priceSpuel = val;
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
  display: block;
}

.info {
  padding: 15px;
  background-color: #7957D5;
  color: white;
  margin-top: 25px;
  margin-bottom: 25px;
}
</style>
