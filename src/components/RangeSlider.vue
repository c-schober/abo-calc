<template>
  <b-field label="Lieferinterval Range">
    <b-slider v-model="endpoints" :max="200" :min="10" :step="1" ticks @input="generateRangeArray">
    </b-slider>
  </b-field>
</template>

<script>
export default {
  name: "RangeSlider",

  data(){
    return {
      endpoints: [],
      range: []
    }
  }

  methods: {
    generateRangeArray(range) {
      console.log(range);
    }
  }
}
</script>

<style scoped>

</style>