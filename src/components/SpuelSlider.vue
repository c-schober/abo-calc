<template>
  <b-field class="slider" label="Anzahl Spülmaschinen/Woche">
    <b-slider v-model="inputSpuel" :max="20" class="slider" tooltip-always
              @input="$emit('calcSpuel', inputSpuel);"></b-slider>
  </b-field>
</template>

<script>
export default {
name: "SpuelSlider",
  data() {
    return {
      inputSpuel: 0
    }
  }
}
</script>

<style scoped>

</style>