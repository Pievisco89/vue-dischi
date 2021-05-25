<template>
  <div>

    <select 
      class="p-2 mb-3" 
      v-model="selectGenre" 
      @click.prevent="getGenre()"
    >
      <option 
        @click.prevent="reset()"
        value=""
      >All genres</option>
      <option 
        v-for="(genre, index) in genres"
        :key="index"
      >{{genre}}</option>
    
    </select>
    
  </div>
</template>

<script>
export default {
  name: 'GenreComp',
  props: {
    genres: Array
  },
  data(){
    return{
      selectGenre: ''
    }
  },
  methods:{
    getGenre(){
      this.$emit("chosenGenre", this.selectGenre);
    },
    reset(){
      this.selectGenre = '';
      this.getGenre();
    }
  }
}
</script>

<style lang="scss" scoped>
  select{
    background-color: #3c3741;
    color: white;
    border-radius: 1.2rem;
    font-size: 1rem;
    cursor: pointer;
    & > option{
      color: rgb(201, 183, 183);
    }
  
  }
</style>