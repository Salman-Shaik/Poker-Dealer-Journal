<template>
  <section class="journal">
    <header>
      <p>Number Of Games Played: {{ numberOfGames }}</p>
      <p>Highest Pot: {{ highestPot }}</p>
    </header>
    <main>
      <table>
        <tr>
          <th><p>Small Blind {{}}</p></th>
          <th><p>Big Blind {{}}</p></th>
          <th>Current Pot</th>
          <th>Total Pot</th>
          <th>Cards Played</th>
          <th>Drop</th>
          <th>Save</th>
        </tr>
        <tr>
          <td>
            <input
              type="text"
              :value="smallBlinds[0] || 0"
              @change="updateSmallBlind"
            />
          </td>
          <td>
            <input type="text" :value="smallBlinds[0] * 2 || 0" />
          </td>
          <td>
            <input type="text" value="0" @change="updateCurrentPot" />
          </td>
          <td>
            <input type="text" v-model="potValue" readonly />
          </td>
          <td>Blind</td>
          <td>
            <players-drop-down v-bind:players="players"></players-drop-down>
          </td>
          <td>
            <save-icon @click="saveRow(0)"></save-icon>
          </td>
        </tr>
        <tr>
          <td>
            <input
              type="text"
              :value="smallBlinds[1] || 0"
              @change="updateSmallBlind"
            />
          </td>
          <td>
            <input type="text" :value="smallBlinds[1] * 2 || 0" />
          </td>
          <td>
            <input type="text" value="0" @change="updateCurrentPot" />
          </td>
          <td>
            <input type="text" v-model="potValue" readonly />
          </td>
          <td>
            <section v-for="index in 3" :key="index">
              <card-number-drop-down></card-number-drop-down>
              <card-symbol-drop-down></card-symbol-drop-down>
            </section>
          </td>
          <td>
            <players-drop-down v-bind:players="players"></players-drop-down>
          </td>
          <td>
            <save-icon @click="saveRow(1)"></save-icon>
          </td>
        </tr>
        <tr>
          <td>
            <input
              type="text"
              :value="smallBlinds[2] || 0"
              @change="updateSmallBlind"
            />
          </td>
          <td>
            <input type="text" :value="smallBlinds[2] * 2 || 0" />
          </td>
          <td>
            <input type="text" value="0" @change="updateCurrentPot" />
          </td>
          <td>
            <input type="text" v-model="potValue" readonly />
          </td>
          <td>
            <section>
              <card-number-drop-down></card-number-drop-down>
              <card-symbol-drop-down></card-symbol-drop-down>
            </section>
          </td>
          <td>
            <players-drop-down v-bind:players="players"></players-drop-down>
          </td>
          <td>
            <save-icon @click="saveRow(2)"></save-icon>
          </td>
        </tr>
        <tr>
          <td>
            <input
              type="text"
              :value="smallBlinds[3] || 0"
              @change="updateSmallBlind"
            />
          </td>
          <td>
            <input type="text" :value="smallBlinds[3] * 2 || 0" />
          </td>
          <td>
            <input type="text" value="0" @change="updateCurrentPot" />
          </td>
          <td>
            <input type="text" v-model="potValue" readonly />
          </td>
          <td>
            <section>
              <card-number-drop-down></card-number-drop-down>
              <card-symbol-drop-down></card-symbol-drop-down>
            </section>
          </td>
          <td>
            <players-drop-down v-bind:players="players"></players-drop-down>
          </td>
          <td>
            <save-icon @click="saveRow(3)"></save-icon>
          </td>
        </tr>
      </table>
      <section>
        Won By: <players-drop-down v-bind:players="players"></players-drop-down>
      </section>
      <section>
        <button class="next_game" @click="startGame">Next Game</button>
        <button class="end_game" @click="startGame">End Game</button>
      </section>
    </main>
  </section>
</template>

<script>
import CardNumberDropDown from "./CardNumberDropDown.vue";
import CardSymbolDropDown from "./CardSymbolDropDown.vue";
import PlayersDropDown from "./PlayersDropdown.vue";
import SaveIcon from "vue-material-design-icons/FastForward.vue";

export default {
  components: {
    CardNumberDropDown,
    CardSymbolDropDown,
    SaveIcon,
    PlayersDropDown,
  },
  data() {
    return {
      currentPot: 0,
      smallBlind: 0,
    };
  },
  methods: {
    updateCurrentPot(event) {
      this.currentPot = +event.target.value;
    },
    updateSmallBlind(event) {
      this.smallBlind = +event.target.value;
    },
    saveRow(index) {
      this.$emit("start", index, this.smallBlind, this.currentPot);
      this.smallBlind = 0;
      this.currentPot = 0;
    },
  },
  props: ["players", "smallBlinds", "potValue", "numberOfGames", "highestPot"],
};
</script>

<style scoped></style>
