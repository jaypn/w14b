<template>
  <div>
    <h1>Welcom to the game</h1>
    <router-link to="/logout">
      <button class="btn" @click="logout">Log out</button>
    </router-link>
 
  <!-- Add a v-if="$store.state.wins < 10" to this block to hide it when game is over -->
    <div  id="choices">
      <button class="btn" @click="select(0)">Rock</button>
      <button class="btn" @click="select(1)">Paper</button>
      <button class="btn" @click="select(2)">Scissors</button>
    </div>
  <!-- Add a block here with a v-if to only show when the game is over -->
  <!-- <div v-if="$store.state.wins == 10">
    <h2>Game Over</h2>
  </div> -->
    <scoreBoard />
    <div id="imageWrapper">
    <userSelection />
    <computerSelction />
    </div>
  </div>
</template>

<script>
import scoreBoard from "../components/scoreBoard";
import userSelection from "../components/userSelection";
import computerSelction from "../components/computerSelection";

export default {
  name: "page-game",
  components: {
    scoreBoard,
    userSelection,
    computerSelction
  },
  data: function() {
    return {
      game_elements: [
        {
          name: "Rock",
          image:
            "https://www.nicepng.com/png/detail/6-61708_rock-rock-paper-scissors-clipart.png"
        },
        {
          name: "Paper",
          image:
            "https://www.clipartkey.com/mpngs/m/109-1094319_rock-paper-scissors-png.png"
        },
        {
          name: "Scissors",
          image:
            "https://www.kindpng.com/picc/m/502-5025794_rock-paper-scissors-clipart-hd-png-download.png"
        }
      ],
      game_rules: {
        Rock: {
          Rock: 0,
          Paper: -1,
          Scissors: 1
        },
        Paper: {
          Rock: 1,
          Paper: 0,
          Scissors: -1
        },
        Scissors: {
          Rock: -1,
          Paper: 1,
          Scissors: 0
        }
      }
    };
  },
  methods: {
    select: function(index) {
      let userSelection = this.game_elements[index];
      let computerSelction = this.game_elements[Math.floor(Math.random() * 3)];
      let result = this.game_rules[userSelection.name][computerSelction.name];
      this.$store.commit("updateUser", userSelection);
      this.$store.commit("updatecomputer", computerSelction);
      this.$store.commit("updateResults", result);
    }
  }
};
</script>

<style scoped>
#imageWrapper{
  display: flex;
  justify-content: space-evenly;
}
</style>