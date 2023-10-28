<template>
<section class="container">
    <h3>Buttle Log</h3>
    <ul>
        <li v-for="log in battleLog" :key="log">
            <span :class="{'log--player': log.attackedBy === 'player', 'log--monster': log.attackedBy === 'monster'}">
                {{ log.attackedBy === 'player' ? "Player " : "Monster "  }}
            </span>
            <span>  {{ log.typeOfAttack === 'attack' ? "attacks by " :
              log.typeOfAttack ==='special-attack' ? "special attacks by " :
              "heals himself for "}}</span>
               <span
              :class="{'log--damage': log.typeOfAttack === 'attack' || log.typeOfAttack === 'special-attack', 'log--heal': log.typeOfAttack === 'heal' }"
              >{{ log.value }}</span
            >
        </li>
    </ul>
</section>    
</template>

<script>
export default {
    props: {
        battleLog: Array
    }
}
</script>

<style scoped>
.container ul{
    text-align: left;
    padding: 0.5rem ;
    list-style: none;
}
.log--player {
  color: #7700ff;
  font-weight: 700;

}

.log--monster {
  color: #da0000;
  font-weight: 700;

}

.log--damage {
  color: red;
  font-weight: 700;
}

.log--heal {
  color: rgb(9, 203, 9);
  font-weight: 700;
}
li{
    padding: 0.3rem 0;
}
</style>