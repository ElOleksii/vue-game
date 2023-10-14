<template>
  <section class="container">
    <h3>Monster Health</h3>
    <div class="healthbar">
      <div :style="updatingMonsterHealthBar" class="healthbar__value"></div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["monsterHealth"],

  computed: {
    updatingMonsterHealthBar() {
      if (this.monsterHealth < 0) {
        return { width: "0%" };
      } else return { width: this.monsterHealth + "%" };
    },
  },
};
</script>

<style></style>
