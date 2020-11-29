<template>
  <b-field class="slider" label="Preis pro 20 Spülmittel-Tabs">
    <b-slider v-model="priceSpuel" :max="20" class="slider" tooltip-always
              @input="$emit('calcPriceSpuel', priceSpuel);"></b-slider>
  </b-field>
</template>

<script>
export default {
  name: "PriceSpuel",
  data() {
    return {
      priceSpuel: 5
    }
  }
}
</script>

<style scoped>

</style>