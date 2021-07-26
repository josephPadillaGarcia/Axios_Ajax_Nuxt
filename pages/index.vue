<template>
<div class="container">
  <header>
    <h1 class="title">Álbums de la página</h1>
  </header>
  <div class="columns is-multiline">
    <AlbumCard :album="album" v-for="album in albums" :key="album.id" />
  </div>
</div>
</template>

<script>
import axios from 'axios'
import env from '../config/env'
import AlbumCard from '../components/AlbumCard'

export default {

  data(){
    return {
      albums: []
    }
  },
  components:{
    AlbumCard
  },
  /*created(){
    axios.get(`${env.endpoint}/albums`).then(response=>{
      console.log(response);
      this.albums = response.data;
    })
  }*/
  created: async function(){
    let albumsResponse = await axios.get(`${env.endpoint}/albums`);
    this.albums = albumsResponse.data;
  }

}
</script>
