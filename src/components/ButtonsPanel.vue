<template>
  <section class="buttons-container">
    <button @click="attackMonster">Attack</button>
    <button :disabled="canUseSpecialAttack" @click="specialAttack">
      Special Attack
    </button>
    <button @click="healPlayer">Heal</button>
    <button>Surround</button>
  </section>
</template>

<script>
import getRandomValue from "@/utils";

export default {
  props: {
    playerHealth: Number,
    monsterHealth: Number,
    currentRound: Number,
  },
  emits: ["update:playerHealth", "update:monsterHealth", "update:currentRound"],
  methods: {
    attackMonster() {
      const attackValue = getRandomValue(8, 18);
      this.$emit("update:playerHealth", this.monsterHealth - attackValue);
      console.log("Emit worked");
      this.attackPlayer();
      this.$emit("update:currentRound", this.currentRound + 1);
    },
    attackPlayer() {
      const attackValue = getRandomValue(8, 18);
      console.log("Emit worked");
      this.$emit("update:monsterHealth", this.playerHealth - attackValue);
    },
    healPlayer() {
      this.availibleHealCount++;

      const healValue = getRandomValue(5, 20);
      this.$emit("update:playerHealth", this.playerHealth + healValue);
    },
    specialAttack() {
      const attackValue = getRandomValue(15, 20);
      this.$emit("update:playerHealth", this.monsterHealth - attackValue);
      this.attackPlayer();
      this.$emit("update:currentRound", this.currentRound + 1);
    },
  },
  computed: {
    canUseSpecialAttack() {
      return this.currentRound % 3 !== 0;
    },
  },
};
</script>

<style scoped>
.buttons-container {
  text-align: center;
  margin: 2rem auto;
  display: grid;
  align-items: center;
  justify-content: center;
  width: 500px;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr);
  gap: 30px;
}
button {
  width: 12rem;
  height: 4rem;
  padding: 1rem 2rem;
  font-size: 1rem;
  cursor: pointer;
  background-color: rgb(203, 92, 0);
  color: #fff;
  border-radius: 15px;
  border: 1px solid rgb(203, 92, 0);
}

button:hover {
  background-color: rgb(230, 92, 0);
}
button:disabled {
  background-color: rgb(83, 83, 83);
  border-color: rgb(83, 83, 83);
}

button:disabled:hover {
  background-color: rgb(104, 104, 104);
}
</style>
