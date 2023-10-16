<template>
  <section class="buttons-container">
    <button @click="attackMonster">Attack</button>
    <button>Special Attack</button>
    <button>Heal</button>
    <button>Surround</button>
  </section>
</template>

<script>
import getRandomValue from "@/utils";

export default {
  props: ["playerHealth, monsterHealth"],
  emits: ["update:playerHealth, update:monsterHealth"],
  methods: {
    attackMonster() {
      const updatedMonsterHealth = this.monsterHealth - getRandomValue(8, 15);
      this.$emit("update:playerHealth", updatedMonsterHealth);
      this.attackPlayer();
    },
    attackPlayer() {
      const updatedPlayerHealth = this.playerHealth - getRandomValue(12, 15);
      this.$emit("update:monsterHealth", updatedPlayerHealth);
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
