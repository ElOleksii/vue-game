<template>
  <section class="container">
    <h3>Your Health</h3>
    <div class="healthbar">
      <div :style="updatingPlayerHealthBar" class="healthbar__value"></div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["playerHealth"],
  computed: {
    updatingPlayerHealthBar() {
      if (this.playerHealth < 0) {
        return { width: "0%" };
      } else return { width: this.playerHealth + "%" };
    },
  },
};
</script>

<style></style>
