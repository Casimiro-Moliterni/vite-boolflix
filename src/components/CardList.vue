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
        <Card v-for="singleCard in store.MovieList" :key="singleCard.id" :MovieInfo="singleCard"></Card>
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
</style>