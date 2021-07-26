<template>
<div>
  <h1>Álbums de la página</h1>
  <div v-for="album in albums" v-bind:key="album.id">
    {{ album.title }}
  </div>
</div>
</template>

<script>
import axios from 'axios'
import env from '../config/env'

export default {

  data(){
    return {
      albums: []
    }
  },

  created(){
    axios.get(`${env.endpoint}/albums`).then(response=>{
      console.log(response);
      this.albums = response.data;
    })
  }

}
</script>
