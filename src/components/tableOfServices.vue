<template>
  <table>
    <thead>
      <tr>
        <th>Наименование</th>
        <th>Цена</th>
        <th>Количество</th>
        <th>Стоимость</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="record of setOfServices" :key="record.id">
        <th>{{ record.nameOfServices }}</th>
        <th>{{ record.price }}</th>
        <th>{{ record.quantity }}</th>
        <th>{{ record.value }}</th>
      </tr>
    </tbody>
    <tr>
      <th></th>
      <th></th>
      <th>Итоговая стоимость:</th>
      <th>{{ totalValue }}</th>
    </tr>
  </table>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "tableOfServices",
  props: {
    setOfServices: {
      type: Object,
      required: true,
    },
    totalValue: {
      type: Number,
      required: false,
      default: 0,
    },
  },
});
</script>

<style scoped>
th {
  width: 150px;
  background-color: rgb(202, 202, 202);
}
</style>
