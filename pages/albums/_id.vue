<template>
  <div class="container">
    <header>
        <nuxt-link to="/">Regresar</nuxt-link>        
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
  created() {
    let albumId = this.$route.params.id;
    axios.get(`${env.endpoint}/albums/${albumId}`).then((albumResponse) => {
      this.contentAlbum = albumResponse.data;
    });
    axios
      .get(`${env.endpoint}/albums/${albumId}/photos`)
      .then((photosResponse) => {
        this.photosAlbum = photosResponse.data;
      });
  },
};
</script>

<style scoped>

    .container{
        text-align: center;
    }

    header{
        margin-top: 50px;
        margin-bottom: 50px;
    }

</style>
