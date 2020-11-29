<template>
  <div>
    <div><label>kleinste Paketgröße Waschmittel: </label>
      <input v-model="packageWash" @input="inputPackageWash()"/>
    </div>
    <div><label>kleinste Paketgröße Spülmittel: </label>
      <input v-model="packageSpuel" @input="inputPackageSpuel()"/>
    </div>
  </div>


</template>

<script>
export default {
  name: "PackageSizeWash",
  data() {
    return {
      packageWash: 19,
      packageSpuel: 20
    }
  },
  methods: {
    inputPackageWash() {
      this.$emit('calcPackageWash', this.packageWash)
    },
    inputPackageSpuel() {
      this.$emit('calcPackageSpuel', this.packageSpuel)
    }
  }
}
</script>

<style scoped>

</style>