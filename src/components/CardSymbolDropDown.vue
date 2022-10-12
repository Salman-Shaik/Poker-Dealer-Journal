<template>
  <select>
    <option value="default" selected disabled>select</option>
    <option value="S">
      <spade-icon></spade-icon>
    </option>
    <option value="H">
      <heart-icon></heart-icon>
    </option>
    <option value="D">
      <diamond-icon></diamond-icon>
    </option>
    <option value="C">
      <club-icon></club-icon>
    </option>
  </select>
</template>

<script>
import SpadeIcon from "vue-material-design-icons/Spade.vue";
import DiamondIcon from "vue-material-design-icons/Diamond.vue";
import HeartIcon from "vue-material-design-icons/Heart.vue";
import ClubIcon from "vue-material-design-icons/Clover.vue";

export default {
  components: {
    SpadeIcon,
    DiamondIcon,
    HeartIcon,
    ClubIcon,
  },
};
</script>

<style scoped></style>
