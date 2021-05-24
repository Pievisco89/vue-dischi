<template>
  <div class="col-sm-6 col-md-3">
    <img :src="album.poster" :alt="album.title">

    <h2> {{album.title}} </h2>
    <h5> {{album.author}} </h5>
    <h6> {{album.year}}</h6>
  </div>
</template>

<script>
export default {
  name: 'AlbumComp',
  props:{
    album: Object
  }
}
</script>

<style>

</style>