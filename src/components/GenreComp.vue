<template>
  <div>

    <select 
      class="p-2 mb-2" 
      v-model="selectGenre" 
      @click.prevent="getGenre()"
    >
      <option disabled value="">Scegli un genere</option>
      <option>Pop</option>
      <option>Rock</option>
      <option >Jazz</option>
      <option>Metal</option>
    </select>
    
  </div>
</template>

<script>
export default {
  name: 'GenreComp',
  data(){
    return{
      selectGenre: ''
    }
  },
  methods:{
    getGenre(){
      this.$emit("chosenGenre", this.selectGenre);
    }
  }
}
</script>

<style lang="scss" scoped>
  select{
    background-color: #3c3741;
    color: white;
    border-radius: 1.2rem;
    font-size: 1rem
  }
</style>