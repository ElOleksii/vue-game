<template>
  <header-top></header-top>
  <monster-health-bar :monsterHealth="monsterHealth"></monster-health-bar>
  <player-health-bar :playerHealth="playerHealth"></player-health-bar>
  <buttons-panel 
  v-model:monsterHealth="monsterHealth"
  v-model:playerHealth="playerHealth"
  v-model:currentRound="currentRound"
  :isGameOver="isGameOver"
  @surround="handleSurround"
  @updateBattleLog="(val) => battleLog = val"
  ></buttons-panel>
  <battle-log :battleLog="battleLog" :isGameOver="isGameOver"></battle-log>
<game-over-popup @new-game="startNewGame" :show="isGameOver" v-if="isGameOver">
<template #outputWinner><h3 :style="gameResultStyles">{{ gameOverStatus }}</h3></template>
</game-over-popup>
</template>

<script>
import HeaderTop from "./components/HeaderTop.vue";
import MonsterHealthBar from "./components/MonsterHealthBar.vue";
import PlayerHealthBar from "./components/PlayerHealthBar.vue";
import ButtonsPanel from "./components/ButtonsPanel.vue";
import BattleLog from "./components/BattleLog.vue";
import GameOverPopup from "./components/GameOverPopup";
export default {
  name: "App",
  components: {
    HeaderTop,
    MonsterHealthBar,
    PlayerHealthBar,
    ButtonsPanel,
    BattleLog,
    GameOverPopup
  },
  data() {
    return {
      playerHealth: 100,
      monsterHealth: 100,
      currentRound: 0,
      isGameOver:false,
      gameOverStatus: null,
      battleLog: [],
    };
  },
  methods: {
    startNewGame(){
    this.playerHealth = 100;
      this.monsterHealth = 100;
      this.currentRound = 0;
      this.battleLog = []
      this.isGameOver = false;
      this.gameOverStatus = null;
      
    }, 
    handleSurround(){
    this.isGameOver = true;
      this.gameOverStatus = "You lost!";
    }
  },
    watch: {
    playerHealth(value) {
      if (value <= 0 && this.monsterHealth <= 0) {
        value = 0;
        this.isGameOver = true;

        this.gameOverStatus = "It's draw!";
      } else if (value <= 0) {
        this.isGameOver = true;

        this.gameOverStatus = "You lost!";
      }
    },
    monsterHealth(value) {
      if (value <= 0) {
        value = 0;
        this.isGameOver = true;

        this.gameOverStatus = "You won!";
      }
    },
},
computed: {
    gameResultStyles(){
        if(this.gameOverStatus === "You lost!"){
            return {"color": "rgb(138, 1, 1)"}
    }
    else if(this.gameOverStatus === "You won!"){
        return {"color": "green"}
    }
    else{
        return {"color": "black"}
    }

    }
},
};
</script>

<style>
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  padding: 10px;
  text-align: center;
  margin: 2rem auto;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  border-radius: 12px;
  width: 750px;
}

.healthbar {
  margin: 1rem auto;
  width: 100%;
  height: 50px;
  border: 1px solid black;
  background-color: rgb(229, 229, 229);
}
.healthbar__value {
  width: 10%;
  background-color: #09c664;
  height: 100%;
}

h3 {
  margin: 0 auto;
  font-size: 1.5rem;
}


</style>
