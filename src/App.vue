<template>
  <HeaderTop></HeaderTop>
  <monster-health-bar></monster-health-bar>
  <player-health-bar></player-health-bar>
  <buttons-panel></buttons-panel>
  <buttle-log></buttle-log>
</template>

<script>
import HeaderTop from './components/HeaderTop.vue'
import MonsterHealthBar from './components/MonsterHealthBar.vue';
import PlayerHealthBar from './components/PlayerHealthBar.vue';
import ButtonsPanel from './components/ButtonsPanel.vue';
import ButtleLog from './components/ButtleLog.vue';
export default {
  name: 'App',
  components: {
    HeaderTop,
    MonsterHealthBar,
    PlayerHealthBar,
    ButtonsPanel,
    ButtleLog
  },


}
</script>

<style>
*, *::after, *::before{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

.container{
    padding: 10px;
    text-align: center;
    margin: 2rem auto;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
    border-radius: 12px;
    width: 750px;
    
}

.healthbar{
    margin: 1rem auto;
    width: 100%;
    height: 50px;
    border: 1px solid black;
    background-color: rgb(229, 229, 229);

}
.healthbar__value{
    width: 10%;
    background-color: #09c664;
    height: 100%;
}

h3{
    margin: 0 auto;
font-size: 1.5rem;
}
</style>
