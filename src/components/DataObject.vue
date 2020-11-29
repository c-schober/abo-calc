<template>
  <div>
    <ul>
      <li style="padding:10px">
        <div class="columns is-multiline is-centered" style="margin-bottom: 1px">
          <div class="interval">Interval in Tagen</div>
          <div class="waschmittel">Waschmittel
          </div>
          <div class="spuelmittel">Spülmittel</div>
          <div class="gesamt">Overdelivery Gesamt
          </div>
          <div class="pricegesamt"> Preis Gesamt
          </div>
        </div>
      </li>
      <li v-for="item in items" :key="item.interval" style="padding:10px">
        <div class="columns is-multiline is-centered" style="margin-bottom: 1px">
          <div :class="{green : item.green}" class="interval">Interval: {{ item.interval }}</div>
          <div :class="{green : item.green}" class="waschmittel"> Benötigte Packs:
            {{ item.neededWashPackages }} | Overdelivery: {{ item.overdeliveryWash }}
          </div>
          <div :class="{green : item.green}" class="spuelmittel"> Benötigte Packs:
            {{ item.neededSpuelPackages }} | Overdelivery: {{ item.overdeliverySpuel }}
          </div>
          <div :class="{green : item.green}" class="gesamt"> Overdelivery Gesamt:
            {{ item.overdeliveryAll }}
          </div>
          <div :class="{sweetspot : item.sweetspot}" class="pricegesamt"> Preis Gesamt:
            {{ item.sum }}
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>

class Obj {
  constructor(interval, minPackageWash, numWash, minPackageSpuel, numSpuel, limit, priceSpuel, priceWash, priceStart, priceEnd) {
    this.interval = interval;
    this.neededWashLoads = interval * numWash / 7;
    this.neededWashPackages = Math.ceil(this.neededWashLoads / minPackageWash);
    this.overdeliveryWash = Math.round((this.neededWashPackages * minPackageWash) - this.neededWashLoads);
    this.neededSpuelLoads = interval * numSpuel / 7;
    this.neededSpuelPackages = Math.ceil((this.neededSpuelLoads / minPackageSpuel) * 2) / 2;
    this.overdeliverySpuel = Math.ceil((this.neededSpuelPackages * minPackageSpuel) - this.neededSpuelLoads);
    this.overdeliveryAll = this.overdeliveryWash + this.overdeliverySpuel;
    this.sum = priceSpuel * this.neededSpuelPackages + priceWash * this.neededWashPackages;
    this.sweetspot = this.sum >= priceStart && this.sum <= priceEnd ? true : false;
    this.green = this.overdeliveryAll <= limit ? true : false;
  }
}


export default {
  name: "DataObject",
  props: ['range', 'numberWash', 'numberSpuel', 'limit', 'priceEndpoints', 'priceWash', 'priceSpuel'],
  data() {
    return {
      items: [],
      packageWash: 19,
      packageSpuel: 20
    }
  },
  watch: {
    range() {
      this.generateObject();
    },
    numberSpuel() {
      this.generateObject();
    },
    numberWash() {
      this.generateObject();
    },
    packageWash() {
      this.generateObject();
    },
    packageSpuel() {
      this.generateObject();
    },
    limit() {
      this.generateObject();
    },
    priceEndpoints() {
      this.generateObject();
    },
    priceWash() {
      this.generateObject();
    }
  },

  methods: {
    generateObject() {
      this.items = [];
      for (let i = 0; i < this.range.length; i++) {
        let x = i + this.range [0];
        let element = new Obj(x, this.packageWash, this.numberWash, this.packageSpuel, this.numberSpuel, this.limit, this.priceSpuel, this.priceWash, this.priceEndpoints[0], this.priceEndpoints[1]);
        this.items.push(element);
      }

    }
  }
}
</script>

<style scoped>

.waschmittel {
  background-color: lightgoldenrodyellow;
  width: 300px;

}

.spuelmittel {
  background-color: lightpink;
  width: 300px;

}

.interval {
  margin-left: 25px;
  background-color: lightblue;
  width: 150px;
}

.gesamt {
  background-color: lightsteelblue;
  width: 300px;
}

.pricegesamt {
  background-color: antiquewhite;
  width: 200px;
}

.green {
  background-color: lawngreen;
}

.sweetspot {
  background-color: limegreen;
  color: white;
}

</style>