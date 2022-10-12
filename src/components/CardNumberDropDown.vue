<template>
  <select>
    <option value="default" selected disabled>select</option>
    <option v-for="index in 13" :key="index" value="getCardNumber(index)">
      {{ getCardNumber(index) }}
    </option>
  </select>
</template>

<script>
export default {
  methods: {
    getCardNumber(index) {
      const number = index;
      if (number === 1) {
        return "A";
      } else if (number === 11) {
        return "J";
      } else if (number === 12) {
        return "Q";
      } else if (number === 13) {
        return "K";
      }
      return number;
    },
  },
};
</script>

<style scoped></style>
