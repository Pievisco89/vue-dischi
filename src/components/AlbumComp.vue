<template>
  <div 
    class="col-sm-4 col-md-2 m-3 p-3 text-center"
  >
    <img 
      class="img-fluid"
      :src="album.poster" 
      :alt="album.title"
    >

    <h2
      class="text-uppercase mt-4"
    > {{album.title}} </h2>
    <h5
      class="mt-5"
    > {{album.author}} </h5>
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

<style lang="scss" scoped>
  div{
    background-color: #3c3741;
    &:hover{
      cursor: pointer;
      transform: scale(1.02);
    }
    img{
      width: 160px;
    }
    h2{
      font-size: 1.25rem;
      color: white;
      font-weight: 800;
      cursor: pointer;
    }
    h5,
    h6{
      color: grey;
      cursor: pointer;
    }
    h5:hover,
    h6:hover{
      color: white;
    }
    
  }
</style>