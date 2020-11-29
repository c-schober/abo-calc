<template>
  <div>
    <button @click="generateObjects()">click</button>
    <ul>
      <li v-for="item in items" :key="item">Interval: {{ item.interval }} | Benötigte Packs:
        {{ item.neededWashPackages }} | Overdelivery: {{item.overdeliveryWash }} |
      </li>
    </ul>
  </div>
</template>

<script>

class Obj {
  constructor(interval, minPackageWash, numberWash, minPackageSpuel, numberSpuel) {
    this.interval = interval;
    this.neededWashLoads = interval * numberWash / 7;
    this.neededWashPackages = Math.ceil(this.neededWashLoads / minPackageWash);
    this.overdeliveryWash = (this.neededWashPackages * minPackageWash) - this.neededWashLoads;
    this.needeSpuelLoads = interval * numberSpuel / 7;
    this.neededSpuelPackages = Math.ceil(this.neededSpuelLoads / minPackageWash);
    this.overdeliveryWash = (this.neededSpuelPackages * minPackageSpuel) - (this.needeSpuelLoads);

  }
}

export default {
  name: "DataObject",
  props: ['range', 'numberWash', 'numberSpuel'],
  data() {
    return {
      packageWash: 20,
      packageSpuel: 10,
      items: []
    }
  },
  methods: {
    generateObjects() {
      this.items = [];
      for (let i = 0; i < this.range.length; i++) {
        let x = i + this.range [0];
        let element = new Obj(x, this.packageWash, this.numberWash, this.packageSpuel, this.numberSpuel);
        this.items.push(element);
      }
    }
  }
}
</script>

<style scoped>

</style>