<template>
  <div id="app">
    <div v-if="!loading">
      <HeaderComp />
    </div>

    <div 
      v-if="!loading"
      class="container text-center p-5"
    >
      <div class="row">

        <AlbumComp 
          v-for="(disc, index) in discs"
          :key="index"
          :album="disc" 
        />
       
      </div>
    </div>

    <div v-else>
      <LoaderComp />
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import HeaderComp from '@/components/HeaderComp.vue';
import AlbumComp from '@/components/AlbumComp.vue';
import LoaderComp from '@/components/LoaderComp.vue';


export default {
  name: 'App',
  data(){
    return {
      axios,
      discs: [],
      loading: true,
    }
  },
  components: {
    AlbumComp,
    HeaderComp,
    LoaderComp
  }, 
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then(resp => {
        this.discs = resp.data.response;
        console.log(resp.data.response);
        setTimeout(()=> {
          this.loading = false;
        }, 2500)
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
