<template>
  <select>
    <option value="default" selected disabled>select</option>
    <option v-for="player in players" value="player">
      {{ player }}
    </option>
  </select>
</template>

<script>
export default {
  props: ["players"],
};
</script>

<style scoped></style>
