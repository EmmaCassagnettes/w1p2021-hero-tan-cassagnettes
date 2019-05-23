<template>
  <div class="suspect">
    <h1 @click="showText" >Suspect {{ name }}</h1><br>
  

     <p>{{ text }}</p>
  </div>
</template>

<style scoped>
.suspect {
  border: solid red 4px;
  color: black;
}
h1 {
   border: solid blue 4px;
}
</style>


<script>
import data from '../assets/data.json';
import audioCount from '../services/audioCount';
import Game from './Game.vue';

export default {
  data() {
    return {
      count: 0,
      text: ''
      
    }
  },
    computed: {
      id() {
        return this.$route.params.id;
      },
      name() {
        return data[this.id].suspects[3].name;
      },
      suspects() {
        return data[this.id].suspects;
      },
      phrases() {
        return data[this.id].suspects.phrases;
      },
  },

  methods: {
    showText() {
      this.text = this.suspects[3].phrases[this.count];
      this.count++;
  
      if(this.count >= this.suspects[3].phrases.length) {
        this.count = 0;
      }

      audioCount.decrement();

      this.$emit('toParent', this.text);
    }
  }
    
};
</script>
