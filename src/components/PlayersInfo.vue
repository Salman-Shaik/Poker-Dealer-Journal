<template>
  <section class="players_info">
    <h4 class="player_info_heading">Enter Player Info</h4>
    <section class="players_input">
      <input
        type="text"
        placeholder="Player Name"
        class="player_name"
        v-model="nameInput"
        @change="onChange"
        autofocus
      />
      <button @click="addPlayer" class="save_player">Enter</button>
    </section>
    <section class="players">
      <span class="player" v-for="player in players">
        <h5 class="player_title">{{ player }}</h5>
        <button @click="removePlayer(player)" class="remove_player">
          <close-icon />
        </button>
      </span>
    </section>
    <button class="start_game" @click="startGame">Start</button>
  </section>
</template>

<script>
import CloseIcon from "vue-material-design-icons/Close.vue";
export default {
  components: {
    CloseIcon,
  },
  data() {
    return {
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
    startGame() {},
  },
  props: ["players"],
};
</script>

<style scoped>
.players_info {
  width: 100vw;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  color: #ffffff;
}
.player_info_heading {
  font-size: 2vw;
  margin-top: 2vw;
}

.players_input {
  display: flex;
  flex-direction: row;
  justify-content: center;
  border-radius: 8px;
  margin-top: 2vw;
}

.player_name,
.save_player,
.player_title,
.remove_player,
.start_game {
  font-size: 1.5vw;
  padding: 0.6vw 1.2vw;
  border: none;
}

.player_name {
  border-top-left-radius: 8px;
  border-bottom-left-radius: 8px;
  color: #222222;
}

.save_player {
  color: white;
  background-color: #666666;
  border-top-right-radius: 8px;
  border-bottom-right-radius: 8px;
}

.save_player:hover {
  background-color: #444444;
}

.players {
  margin-top: 2vw;
  padding: 1vw;
  display: grid;
  grid-auto-rows: 1fr;
  grid-template-rows: 1fr 1fr 1fr 1fr 1fr;
  grid-template-columns: 1fr 1fr 1fr 1fr 1fr;
  gap: 1vw 1vw;
  grid-template-areas:
    ". . . . ."
    ". . . . ."
    ". . . . .";
}

.player {
  display: flex;
  flex-direction: row;
  justify-content: center;
  background: #666666;
  border-radius: 8px;
}

.remove_player {
  background: none;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  justify-self: flex-end;
}

.player_title,
.remove_player {
  padding: 0.2vw 0.6vw;
}

.start_game {
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
  border-radius: 8px;
  width: 10vw;
}
</style>
