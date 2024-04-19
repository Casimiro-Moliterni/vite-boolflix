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
            <h1 v-if="store.searchText.length > 0">FILM</h1>
            <h1 v-else>FILM POPOLARI</h1>
        </div>
        <div  class="wrapper-list">
        <Card  v-for="singleCard in store.MovieList" :key="singleCard.id" :MovieInfo="singleCard"  ></Card>
       </div>
    </div>
    <div class="container">
        <div class="wrapper-title">
          <h1 v-if="store.searchText.length > 0">SERIE TV</h1>
          <h1 v-else>SERIE TV POPOLARI</h1>  
        </div>
        <div class="wrapper-list">
          <Card  v-for="singleCard in store.SerieTvList" :key="singleCard.id" :MovieInfo="singleCard"  ></Card>
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
            box-shadow: rgba(0, 0, 0, 0.56) 0px 22px 70px 4px;
            box-shadow: rgba(0, 0, 0, 0.25) 0px 30px 60px -12px inset, rgba(0, 0, 0, 0.3) 0px 18px 36px -18px inset;
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