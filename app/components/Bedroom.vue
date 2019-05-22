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
       
       
    </section>
    <router-link class="button" to="/game/1">Retour au salon</router-link>

  
    <Tools></Tools>
  </div>
</template>

<style scoped>
  .picture {
    display: flex;
  }
  .picture {
    border: solid 3px red;
    background-color: yellow;
    width: 150px;
    height: 150px;
  }
  img {
    border : solid 4px black;
    width: 100px;
    height: 100px;
  }
</style>


<script>
import data from '../assets/data.json';
import audioCount from '../services/audioCount';
import Tools from '../components/Tools.vue';

export default {
    data() {
      return {
        count : 0,
        images: [
          'http://via.placeholder.com/350x150',
          'http://via.placeholder.com/200x140',
          'http://via.placeholder.com/200x100'
        ],
          selectedImage: 'https://static.thenounproject.com/png/393234-200.png',
          selectedImage1: 'https://static.thenounproject.com/png/393234-200.png',
          selectedImage2: 'https://static.thenounproject.com/png/393234-200.png'
      }
    },
    components: {
      Tools
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
      }

    }
  
  } 

</script>
