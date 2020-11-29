<template>
  <b-field class="slider" label="Anzahl Wäschen/Woche">
    <b-slider v-model="inputWash" :max="20" class="slider" tooltip-always
              @input="$emit('calcWash', inputWash);"></b-slider>
  </b-field>
</template>

<script>
export default {
  name: "WashSlider",
  data() {
    return {
      inputWash: 0
    }
  }
}
</script>

<style scoped>

</style>