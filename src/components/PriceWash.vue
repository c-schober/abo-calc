<template>
  <b-field class="slider" label="Preis pro 19 Waschladungen">
    <b-slider v-model="priceWash" :max="20" class="slider" tooltip-always
              @input="$emit('calcPriceWash', priceWash);"></b-slider>
  </b-field>
</template>

<script>
export default {
  name: "PriceWash",
  data() {
    return {
      priceWash: 12
    }
  }
}
</script>

<style scoped>

</style>