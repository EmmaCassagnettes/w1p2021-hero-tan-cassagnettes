<template>
  <div class="big-header">
    <h1>Choisis ta détective</h1>
    <br />

    <section class="players">
      <div @click="choicePlayer1" class="player player1">Emmaaa</div>
      <div @click="choicePlayer2" class="player player2">Amandaaa</div>
    </section>
    
    <template v-if="showPlay === true">
      <router-link class="button" to="/game/1">Jouer</router-link>
    </template>

    


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
  data() {
    return {
      character: ''
    }
  },
  computed: {
    showPlay() {
      // if(!localStorage.getItem('character')) {
      //   //console.log('choix fait');
      //   return false;
      // } 
      if(this.character != '') {
        return true;
      }
    }
  },
  methods: {
    choicePlayer1(){
      audioCount.increment();
      this.character = 'Emma';
      localStorage.setItem('character', 'Emma');
    },
     choicePlayer2(){
      //audioCount.increment();
      this.character = 'Amanda';
      localStorage.setItem('character', 'Amanda');
    }
  //   // showPlay() {
  //   //   if(localStorage.getItem('character')) {
  //   //     //console.log('choix fait');
  //   //     return true;
  //   //   } 
  //   // }
  // }
  }
}
</script>
