<template>
  <div class="big-header">
    <h1>Choisis ta détective</h1>
    <br />

  <div class="choice">
    <img src="../assets/images/detective.png">
    <img src="../assets/images/Joan_Hickson.jpg">
  </div>

    <section class="players">
      <div class="player">
        <div @click="choicePlayer1" class="player1">Emmaaa</div>
        <div>Picto skill</div>
        <div>Fine détective, aux questions aussi précises que subtiles, son air angélique saura vous envoûter et vous faire parler, afin d'obtenir des aveux de vous. Son point fort, l'écoute et la persévérance</div>
      </div>

      <div class="player">
        <div @click="choicePlayer2" class="player2">Amandaaa</div>
        <div>Picto</div>
        <div>L'observation et le feeling sont ses leitmotiv. Plutôt du style à vivre au jour le jour, à prendre tous les risques sans se soucier du lendemain, elle n'a pas froid aux yeux... d'ailleurs, on l'appelle l'oeil de lynx dans le milieux</div>
      </div>
      
      
    </section>
    
    <template v-if="showPlay === true">
      <router-link class="button" to="/game/1">Jouer</router-link>
    </template>

    
     <div class="music">
      <audio autoplay loop id="player" src="../assets/images/vuejs_projet_sound3.mp3"></audio>
    <div> 
    <button class="button" onclick="document.getElementById('player').play()">Sound on</button> 
    <button class="button" onclick="document.getElementById('player').pause()">Sound off</button> 
      </div>
    </div>

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
import Bedroom from '../components/Bedroom.vue';

export default {
  data() {
    return {
      character: ''
    }
  },
  computed: {
    showPlay() {
      if(this.character != '') {
        return true;
      }
    }
  },
  methods: {
    choicePlayer1(){
      //audioCount.increment();
      audioCount.setvalue(12)
      this.character = 'Emma';
      localStorage.setItem('character', 'Emma');
    },
     choicePlayer2(){
      //audioCount.increment();
      audioCount.setvalue(10);
      this.character = 'Amanda';
      localStorage.setItem('character', 'Amanda');
    }
  }
}
</script>
