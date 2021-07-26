<template>
  <div class="container">
    <header>
        <nuxt-link to="/" class="button is-primary">Regresar</nuxt-link>        
        <h1 class="title">{{ contentAlbum.id }} : {{ contentAlbum.title }}</h1>
    </header>
    <div class="columns is-multiline">
      <div
        class="column is-one-quarter"
        v-for="photo in photosAlbum"
        :key="photo.id"
      >
        <img :src="photo.url" :alt="photo.title" />
      </div>
    </div>
  </div>
</template>

<script>
import router from "vue-router";
import axios from "axios";
import env from "../../config/env";

export default {
  name: "AlbumIndvPage",
  data() {
    return {
      alId: "",
      contentAlbum: {},
      photosAlbum: {},
    };
  },
  /*created() {
    let albumId = this.$route.params.id;
    axios.get(`${env.endpoint}/albums/${albumId}`).then((albumResponse) => {
      this.contentAlbum = albumResponse.data;
    });
    axios
      .get(`${env.endpoint}/albums/${albumId}/photos`)
      .then((photosResponse) => {
        this.photosAlbum = photosResponse.data;
      });
  }*/
   created: async function(){
      let albumResponse = await axios.get(`${env.endpoint}/albums/${this.$route.params.id}`);
      this.contentAlbum = albumResponse.data; 
      let photosResponse = await  axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`);
      this.photosAlbum = photosResponse.data;
  }
};
</script>

<style scoped>

    .container{
        text-align: center;
    }

</style>
