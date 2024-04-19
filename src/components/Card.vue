<script>
import { store } from '../store.js';
export default{
    name:'Card',
    data(){
        return{
            store,
            flagsArray:[
                'it',
                'fr',
                'de',
                'en',
                'jp',
                'es'
            ]
        }
    },
    props: {
        MovieInfo: Object
    },
    methods:{
        getImageUrl(name) {
                return `https://image.tmdb.org/t/p/w342${name}` ;
            },
            getImageFlag() {
                let flag = this.MovieInfo.original_language + '.png';
                return new URL(`../assets/img/${flag}`, import.meta.url).href;
            },
            fixNumber(number){
                if(number > 0){
                    number= number/2;
                }
                return number.toFixed();
            }
    },
}
</script>

<template>
   <div class="single-card">
    <!-- img  -->
    <div class="image-poster" >
        <img v-if="MovieInfo.poster_path !== null" :src="getImageUrl(MovieInfo.poster_path)" alt="">
        <img v-else src="../assets/img/null.png" alt="">

    </div>
    <!-- title  -->
     <h3 class="p-b">Titolo: {{ MovieInfo.title ? MovieInfo.title : MovieInfo.name}}</h3>
     <!-- original title  -->
     <h3 class="p-b">Titolo Orginale: {{ MovieInfo.original_title ? MovieInfo.original_title : MovieInfo.original_name }}</h3>
     <!-- flags  -->
     <div class="p-b image flag" v-if="flagsArray.includes(MovieInfo.original_language)" >
        <img :src="getImageFlag()" alt="">
    </div>
    <!-- original_language  -->
     <h4 class="p-b" v-else>Lingua:{{ MovieInfo.original_language }}</h4>
     <!-- vote  -->
     <h4 class="p-b">Voto: {{ fixNumber(MovieInfo.vote_average)  }}</h4>
   </div>
</template>

<style scoped lang="scss">
    .single-card{
        color: white;
        position: relative;
        background-color:rgb(69, 66, 66);
        text-align: center;
        border: 1px solid black;
        box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px, rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px, rgba(0, 0, 0, 0.17) 0px 12px 13px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
        border-radius: 4px;
        width: calc((100% / 5 ) - 10px);
        margin: 5px;
        .image.flag{
            width: 10%;
            margin: 0 auto;
           img{
            object-fit: cover;
            width: 100%;
            height: 20px;
           }
        }
        .image-poster{
          
           img{
           
            object-fit: cover;
            width: 100%;
            min-height: 500px;
           }
        }
        h2,h3,h4{
           
        }
    }
    .p-b{
        padding-bottom: 10px;
    }
</style>