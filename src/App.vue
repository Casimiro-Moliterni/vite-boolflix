<script>
import { store } from './store.js';
import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import CardList from './components/CardList.vue';

export default {
   
  components:{
    AppHeader,
    CardList
  },
  data(){
    return{
      store
    }
  },
  methods:{
    getCharactersFromApi(){
      
      const queryParams ={

      };

      if(store.searchText !== ''){
        queryParams.query = store.searchText
      }
      // axios api 
       axios.get('https://api.themoviedb.org/3/search/movie?api_key=8553ca13f1428eb8af642e1115ad4dc1',{
        params:queryParams
       })
       .then((response)=>{
        store.MovieList = response.data.results;
        console.log(store.MovieList)
       })
    }
  },
  mounted(){
    this.getCharactersFromApi()
  }
}
</script>

<template>
 <AppHeader @searchPerfomed="getCharactersFromApi()"></AppHeader>
 <main>
  <CardList></CardList>
</main>
</template>
<style lang="scss">
@use './style/generic';
</style>