<script>
import { store } from '../store.js';
import Card from './Card.vue';
export default{
    name:'CardList',
    components:{
       Card
    },
    data(){
        return{
            store
        }
    }
}
</script>

<template>
 <section>
    <div class="container">
        <div class="wrapper-title">
            <h1 v-if="store.MovieList.length > 0">FILM</h1>
        </div>
        <div  class="wrapper-list">
        <Card  v-for="singleCard in store.MovieList" :key="singleCard.id" :MovieInfo="singleCard"  ></Card>
       </div>
    </div>
    <div class="container">
        <div class="wrapper-title">
          <h1 v-show="store.SerieTvList.length > 0">SERIE TV</h1>  
        </div>
        <div class="wrapper-list">
          <Card  v-for="singleCard in store.SerieTvList" :key="singleCard.id" :SerieInfo="singleCard"  ></Card>
       </div>
    </div>
 </section>
</template>

<style scoped lang="scss">
.wrapper-list{
    display: flex;
    flex-wrap:wrap ;
    justify-content: flex-start;
    margin-bottom: 30px;
}
section{
    color: white;
    padding-top:30px ;
    background-color:#1B1B1B;
    
    .wrapper-title{
        display: flex;
        justify-content: center;
        h1{
         text-align: center;
        margin: 0 0 30px 10px;
        font-size: 30px;
        background-color: red;
        border-radius: 3px;
        padding: 5px 0;
        width: 30%;
    }
    }
}
</style>