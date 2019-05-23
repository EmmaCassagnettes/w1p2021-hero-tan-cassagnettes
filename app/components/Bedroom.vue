<template>
  <div class="big-header">
    <h1>Chambre</h1>
    <br />
    <section class="pictures">
      <div class="picture" @click="showPicture">
        <img v-bind:src="selectedImage"/>
      </div>
      <div class="picture">
        <img v-bind:src="selectedImage1" @click="showPicture1"/>
      </div>
      <div class="picture">
        <img v-bind:src="selectedImage2" @click="showPicture2"/>
      </div>
      <div class="picture">
        <img v-bind:src="selectedImage3" v-if="showPicturePlayer2 === true"/>
      </div>
      <div class="picture">
        <img v-bind:src="selectedImage4" @click.once="randomImage2"/>
      </div>
      
       
       
    </section>
    <router-link class="button" to="/game/1">Retour au salon</router-link>

  
    <Tools></Tools>
  </div>
</template>

<style scoped>
  .pictures {
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 10px;
    position: absolute;
    right: 60px;
    border: solid 3px blue;
  }
  .picture {
    border: solid 3px red;
    background-color: yellow;
    width: 200px;
    height: 200px;
  }
  img {
    border : solid 4px black;
    width: 100px;
    height: 100px;
  }
  .button {
    position: absolute;
    left: 60px;
  }
</style>


<script>
import data from '../assets/data.json';
import audioCount from '../services/audioCount';
import Tools from '../components/Tools.vue';
import Character from '../components/Character.vue';

export default {
    data() {
      return {
        count : 0,
        character : localStorage.getItem('character'),
        images: [
          'http://via.placeholder.com/350x150',
          'http://via.placeholder.com/200x140',
          'http://via.placeholder.com/200x100'
        ],
        selectedImage: 'https://static.thenounproject.com/png/393234-200.png',
        selectedImage1: 'https://static.thenounproject.com/png/393234-200.png',
        selectedImage2: 'https://static.thenounproject.com/png/393234-200.png',
        selectedImage3: 'https://static.thenounproject.com/png/393234-200.png',
        selectedImage4: 'https://static.thenounproject.com/png/393234-200.png'
      }
    },
    components: {
      Tools,
      Character
    },
    computed:{
      showPicturePlayer2(){
        if(this.character === 'Amanda') {
          return true;
        }
      }
    },
    mounted() {
      if(localStorage.getItem('image1')){
          this.selectedImage = localStorage.getItem('image1');
      }
      if(localStorage.getItem('image2')){
          this.selectedImage1 = localStorage.getItem('image2');
      }
      if(localStorage.getItem('image3')){
          this.selectedImage2 = localStorage.getItem('image3');
      }
      if(localStorage.getItem('image4')) {
          this.selectedImage4 = localStorage.getItem('image4');
      }
      

    },
    methods: {

      showPicture() {
        this.selectedImage = this.images[0];
        localStorage.setItem('image1', this.selectedImage);
      },
      showPicture1() {
        this.selectedImage1 = this.images[1];
        localStorage.setItem('image2', this.selectedImage1);
      },
      showPicture2() {
        this.selectedImage2 = this.images[2];
        localStorage.setItem('image3', this.selectedImage2);
      },
      // showPicturePlayer2(){
      //   if(localStorage.getItem('character') === 'Amanda') {
      //     return true;
      //   }
      // }
      randomImage2 () {
        const idx = Math.floor(Math.random() * this.images.length);
        this.selectedImage4 = this.images[idx];
        localStorage.setItem('image4', this.selectedImage4);
        
      }
    }
  
  } 

</script>
