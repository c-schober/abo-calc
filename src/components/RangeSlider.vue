<template>
  <b-field class="slider" label="Lieferinterval Test-Range in Tagen">
    <b-slider v-model="endpoints" :max="200" :min="10" :step="1" ticks @input="generateRangeArray">
    </b-slider>
  </b-field>
</template>

<script>
export default {
  name: "RangeSlider",

  data(){
    return {
      range: [],
      endpoints: [],
    }
  },

  methods: {
    generateRangeArray(range) {
      this.range = [];
      let i;
      for (i = range[0]; i <= range[1]; i++) {
        this.range.push(i);
      }
      this.$emit('intervalRange', this.range);
    }
  }
}
</script>

<style scoped>

</style>