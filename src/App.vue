<template>
  <div id="app">
    <RangeSlider />
  </div>
</template>

<script>

import RangeSlider from "@/components/RangeSlider";
export default {
  name: 'App',
  components: {
    RangeSlider
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
