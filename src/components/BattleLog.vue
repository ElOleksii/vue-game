<template>
<section class="container">
    <h3>Buttle Log</h3>
    <ul>
        <li v-for="log in battleLog" :key="log">
            {{ log }}
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
</style>