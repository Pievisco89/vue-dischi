<template>
  <div id="app">

    <div class="container text-center mt-35">

      <h2>Dischi</h2>

      <div class="row">
        <AlbumComp 
          v-for="(disc, index) in discs"
          :key="index"
          :album="disc" 
        />
       
      </div>
    </div>

  </div>
</template>

<script>
import axios from 'axios';
import AlbumComp from '@/components/AlbumComp.vue';


export default {
  name: 'App',
  data(){
    return {
      axios,
      discs: []
    }
  },
  components: {
    AlbumComp,
  }, 
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then(resp => {
        this.discs = resp.data.response;
        console.log(resp.data.response);
      })
      .catch(err => {
        console.log(err);
      })
  },
  
}
</script>

<style lang="scss">
  @import '@/assets/style/general.scss';

</style>
