<script>
import PlayersInfo from "./components/PlayersInfo.vue";

export default {
  name: "app",
  components: {
    PlayersInfo,
  },
};
</script>

<template>
  <header>
    <h1>Poker Dealer Journal</h1>
  </header>

  <main>
    <players-info></players-info>
    <section class="journal"></section>
    <section class="stats"></section>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
