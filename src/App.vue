<template>
  <div id="app">
    <div v-if="!loading">
      <HeaderComp />

    </div>

    <div 
      v-if="!loading"
      class="container p-5"
    >
      <div class="row">
        
        <GenreComp 
          @chosenGenre="musicGenre"
        />

        <AlbumComp 
          v-for="(disc, index) in filteredDiscs"
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
import GenreComp from '@/components/GenreComp.vue';



export default {
  name: 'App',
  data(){
    return {
      axios,
      discs: [],
      genres: [],
      loading: true,
      genreText: ''
    }
  },
  components: {
    AlbumComp,
    HeaderComp,
    LoaderComp,
    GenreComp
  }, 
  created(){
    axios.get('https://flynn.boolean.careers/exercises/api/array/music')
      .then(resp => {
        this.discs = resp.data.response;
        resp.data.response.forEach(item => {
          if (!this.genres.includes(item.genre)) {
            this.genres.push(item.genre);
          }
          console.log(this.genres);
        });
        console.log(resp.data.response);
        /* setTimeout(()=> {
          this.loading = false;
        }, 1000) */
        this.loading = false;
      })
      .catch(err => {
        console.log(err);
      })
  },
  methods:{
    musicGenre(text){
      this.genreText = text;
    }
  },
  computed:{
    filteredDiscs(){

      if(this.genreText === ''){
        return this.discs;
      }
      
      return this.discs.filter(item => this.genreText === item.genre)
      
    }

  }
}
</script>

<style lang="scss">
  @import '@/assets/style/general.scss';

</style>
