<template>
  <b-field class="slider" label="Highlighted Preis Limit Range">
    <b-slider v-model="priceEndpoints" :max="150" :min="1" :step="1" ticks @input="generatePriceLimit">
    </b-slider>
  </b-field>
</template>

<script>
export default {
  name: "PriceLimit",

  data(){
    return {
      priceEndpoints: [],
    }
  },

  methods: {
    generatePriceLimit() {
      this.$emit('calcPriceEndpoints', this.priceEndpoints);
    }
  }
}
</script>

<style scoped>

</style>