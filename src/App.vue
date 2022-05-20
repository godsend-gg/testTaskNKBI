<template>
  <generateButton @generate="generate" />
  <tableOfServices
    :setOfServices="setOfServices"
    :totalValue="totalValue"
    v-if="setOfServices.length"
  />
</template>

<script lang="ts">
import { defineComponent } from "vue";
import tableOfServices from "./components/tableOfServices.vue";
import generateButton from "./components/generateButton.vue";

interface MyObj {
  nameOfServices: string;
  price: number;
  quantity: number;
  value: number;
}

export default defineComponent({
  name: "App",
  components: {
    tableOfServices,
    generateButton,
  },
  data() {
    return {
      setOfServices: [] as MyObj[],
      totalValue: 0,
    };
  },
  methods: {
    generate() {
      this.setOfServices = [];
      for (let i = 0; i < 50; i++) {
        var randomName = "";
        while (randomName.length < 5) {
          randomName += String.fromCharCode(Math.random() * 1106).replace(
            /[^а-я]|_/g,
            ""
          );
        }
        var price = this.normalizeNumber(Math.random() * 1000);
        var quantity: number = Math.floor(Math.random() * 100) + 1;
        var value = this.normalizeNumber(quantity * price);
        this.totalValue = this.normalizeNumber(this.totalValue + value);
        var tableRow: MyObj = {
          nameOfServices: randomName,
          price: price,
          quantity: quantity,
          value: value,
        };
        this.setOfServices.push(tableRow);
      }
    },
    normalizeNumber(number: number) {
      return Number(number.toFixed(2));
    },
  },
});
</script>
<style>
#app {
  display: grid;
  justify-content: center;
}
button {
  width: 200px;
  justify-self: center;
}
</style>
