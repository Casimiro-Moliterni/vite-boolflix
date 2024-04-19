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
      store,
      ApiUrlMovie :'https://api.themoviedb.org/3/search/movie',
      ApiUrlSerie :'https://api.themoviedb.org/3/search/tv',
    }
  },
  methods:{
    getMovieFromApi(){
  
      const queryParams ={
      language:'it-IT',
      api_key:'8553ca13f1428eb8af642e1115ad4dc1',
      };

      if(store.searchText !== ''){
        queryParams.query = store.searchText
      }
      // axios api movie
       axios.get(this.ApiUrlMovie ,{
          params:queryParams
        })
       .then((response)=>{
           store.MovieList = response.data.results; 
           console.log(response.data.results)
        })
      //  axios serie 
       axios.get(this.ApiUrlSerie,{
          params:queryParams
          })
       .then((response)=>{
          store.SerieTvList = response.data.results; 
          console.log(response.data.results)
          })
    }
  
  },
  mounted(){
    axios.get('https://api.themoviedb.org/3/movie/popular?api_key=8553ca13f1428eb8af642e1115ad4dc1&language=its-US&page=1')
    .then((response)=>{
           store.MovieList = response.data.results; 
           console.log(response.data.results)
        }),
        axios.get('https://api.themoviedb.org/3/tv/popular?api_key=8553ca13f1428eb8af642e1115ad4dc1&language=its-US&page=1')
    .then((response)=>{
           store.SerieTvList = response.data.results; 
           console.log(response.data.results)
        })
  }
}
</script>

<template>
 <AppHeader @searchPerfomedMovie="getMovieFromApi()"></AppHeader>
 <main>
  <CardList></CardList>
</main>
</template>
<style lang="scss">
@use './style/generic';
</style>