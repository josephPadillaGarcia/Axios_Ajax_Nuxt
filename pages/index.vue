<template>
<div>
  <h1>Álbums de la página</h1>
  <AlbumCard :album="album" v-for="album in albums" :key="album.id" />
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
  created(){
    axios.get(`${env.endpoint}/albums`).then(response=>{
      console.log(response);
      this.albums = response.data;
    })
  }

}
</script>
