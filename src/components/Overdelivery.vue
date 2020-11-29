<template>
  <b-field class="slider" label="Highlighted Overdelivery Limit">
    <b-slider v-model="inputLimit" :max="40" class="slider" tooltip-always
              @input="$emit('calcLimit', inputLimit);"></b-slider>
  </b-field>
</template>

<script>
export default {
  name: "Overdelivery",
  data() {
    return {
      inputLimit: 5
    }
  }
}
</script>

<style scoped>

</style>