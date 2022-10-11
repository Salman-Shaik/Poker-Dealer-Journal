<template>
  <section class="players-info">
    <h4>Players</h4>
    <section class="players-input">
      <input
        type="text"
        placeholder="Player Name"
        v-model="nameInput"
        @change="onChange"
        autofocus
      />
      <button @click="addPlayer">Enter</button>
    </section>
    <section class="players" v-for="player in players">
      <span>
        <h5>{{ player }}</h5>
        <button @click="removePlayer(player)">X</button>
      </span>
    </section>
    <button>Start</button>
  </section>
</template>

<script>
export default {
  data() {
    return {
      players: [],
      nameInput: "",
    };
  },
  methods: {
    onChange(event) {
      const playerName = event.target.value;
      this.nameInput = playerName;
    },
    addPlayer() {
      this.players.push(this.nameInput);
      this.nameInput = "";
    },
    removePlayer(player) {
      const playerIndex = this.players.indexOf(player);
      this.players.splice(playerIndex, 1);
    },
  },
};
</script>
