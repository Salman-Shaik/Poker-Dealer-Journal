<script>
import PlayersInfo from "./components/PlayersInfo.vue";
import Journal from "./components/Journal.vue";

export default {
  name: "app",
  components: {
    PlayersInfo,
    Journal,
  },
  data() {
    return {
      players: [],
      gameStatus: "",
      smallBlinds: [],
      potValue: 0,
      numberOfGames: 0,
      highestPot: 0,
    };
  },
  methods: {
    startGame() {
      this.gameStatus = "STARTED";
    },
    saveGameRow(index, smallBlind, currentPot) {
      this.smallBlinds[index] = smallBlind;
      this.potValue = this.potValue + currentPot;
    },
  },
};
</script>

<template>
  <header>
    <h1>Poker Dealer Ledger</h1>
  </header>

  <main>
    <players-info
      v-if="!gameStatus"
      @start="startGame"
      v-bind:players="players"
    >
    </players-info>
    <journal
      v-else-if="gameStatus === 'STARTED'"
      @save="saveGameRow"
      v-bind:players="players"
      v-bind:potValue="potValue"
      v-bind:highestPot="highestPot"
      v-bind:smallBlinds="smallBlinds"
      v-bind:numberOfGames="numberOfGames"
    ></journal>
    <section class="stats" v-else></section>
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
    justify-content: center;
    align-items: center;
    padding-right: calc(var(--section-gap) / 2);
    background: #a8ff78; /* fallback for old browsers */
    background: -webkit-linear-gradient(
      to right,
      #78ffd6,
      #a8ff78
    ); /* Chrome 10-25, Safari 5.1-6 */
    background: linear-gradient(
      to right,
      #78ffd6,
      #a8ff78
    ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
    color: #222222;
    width: 100vw;
    font-size: 2.2vw;
    padding: 4vh 0;
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
  main {
    width: 100vw;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
  }
}
</style>
