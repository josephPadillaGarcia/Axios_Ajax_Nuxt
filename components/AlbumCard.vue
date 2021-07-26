<template>
    <div class="box column is-one-quarter">
        <h3>{{ album.title }}</h3>
        <a href="#">Ver Álbum</a>
    </div>
</template>

<script>

export default {
    name: 'AlbumCard',
    props:{
        album:Object
    }
}
</script>

<style scoped>

    .box{
        padding: 1em !important;
    }

</style>
