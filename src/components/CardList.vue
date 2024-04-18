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
        <div  class="wrapper-list">
        <Card  v-for="singleCard in store.MovieList" :key="singleCard.id" :MovieInfo="singleCard"  ></Card>
        <Card  v-for="singleCard in store.SerieTvList" :key="singleCard.id" :SerieInfo="singleCard"  ></Card>
    </div>
    </div>
 </section>
</template>

<style scoped lang="scss">
.wrapper-list{
    display: flex;
    flex-wrap:wrap ;
    justify-content: space-between;
}
section{
    padding-top:20px ;
    background-color:#1B1B1B;
    
}
</style>