<template>
  <div class="big-header">
    <h1>Chambre</h1>
    <br />
    <section class="pictures">
      <div class="picture" @click="showPicture">
        <!-- <img v-bind:src="selectedImage" @click.once="randomImage"/> -->
        <img v-bind:src="selectedImage"/>
      </div>
      <div class="picture">
        <img v-bind:src="selectedImage1" @click.once="randomImage1"/>
      </div>
      <div class="picture">
        <img v-bind:src="selectedImage2" @click.once="randomImage2"/>
      </div>
       
       
    </section>
    <router-link class="button" to="/game/1">Retour au salon</router-link>

    <!-- <router-view name="tools">coucou</router-view> -->
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
        selectedImage: '',
        selectedImage1: 'https://static.thenounproject.com/png/393234-200.png',
        selectedImage2: 'https://static.thenounproject.com/png/393234-200.png'
    }
  },
  components: {
    Tools
  },
  mounted() {
    // if(localStorage.getItem('image1')){
    //   try {
    //     this.selectedImage = JSON.parse(localStorage.getItem('image1'));
    //   } catch(e) {
    //     localStorage.removeItem('image1');
    //   }
    // }

    if(localStorage.getItem('image1')){
        this.selectedImage = localStorage.getItem('image1');
    }
  },
    methods: {
    // showPicture() {
    //   return false;
    // },
    showPicture() {
      this.selectedImage = 'http://via.placeholder.com/350x150';
      localStorage.setItem('image1', this.selectedImage);
    },
    // randomImage() {
    //   const idx = Math.floor(Math.random() * this.images.length);
    //   this.selectedImage = this.images[idx];

    //   localStorage.setItem('image1', this.selectedImage);
    // },
    // randomImage1 () {
    //   const idx = Math.floor(Math.random() * this.images.length);
    //   this.selectedImage1 = this.images[idx];

    //   localStorage.setItem('image2', this.selectedImage1);
    // },
    randomImage2 () {
      const idx = Math.floor(Math.random() * this.images.length);
      this.selectedImage2 = this.images[idx];

    //   localStorage.setItem('image3', this.selectedImage2);

    //   if(localStorage.getItem('image3')) {
    //     this.selectedImage2 = localStorage.getItem('image3');
    //   }
    // }
    }
    // savePicture() {
    //   const parsed = JSON.stringify(this.selectedImage);
    //   localStorage.setItem('image1', parsed);
    // }
  } 
} 
</script>
