<template>
  <div class="big-header">
    <h1>Choisir son personnage</h1>
    <br />

    <section class="players">
      <div @click="choicePlayer1" class="player player1">Emma</div>
      <div class="player player2">Amandaaa</div>
    </section>
    


    <router-link class="button" to="/game/1">Jouer</router-link>
  </div>
</template>

<style scoped>
.players {
  display: flex;
}

.player {
  border: solid 3px black;
  margin: 20px;
  width: 200px;
  height: 200px;
}
</style>



<script>
import data from '../assets/data.json';
import audioCount from '../services/audioCount';

export default {
  methods: {
    choicePlayer1(){
      audioCount.increment();
    }
  }
};
</script>
