<script>
import { store } from '../store.js';
export default {
    name: 'Card',
    data() {
        return {
            store,
            flagsArray: [
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
    methods: {
        getImageUrl(name) {
            return `https://image.tmdb.org/t/p/w342${name}`;
        },
        getImageFlag() {
            let flag = this.MovieInfo.original_language + '.png';
            return new URL(`../assets/img/${flag}`, import.meta.url).href;
        },
        getStar() {
           
            return Math.ceil(this.MovieInfo.vote_average / 2);
        },
       
    }
}
</script>

<template>
    <div class="single-card" >
        <!-- img  -->
        <div class="card" >
            <div class="image-poster default" v-if="MovieInfo.poster_path !== null">
            <img  :src="getImageUrl(MovieInfo.poster_path)" alt="">
        </div>
        <div class="image-poster null" v-else>
            <img  src="../assets/img/null.png" alt="">
            <div>{{MovieInfo.title ? MovieInfo.title : MovieInfo.name}}</div>
        </div>
        <!-- title  -->
        <div class="wrapper-text">
            <h3 class="p-b">Titolo: {{ MovieInfo.title ? MovieInfo.title : MovieInfo.name }}</h3>
            <!-- original title  -->
            <h3 class="p-b">Titolo Orginale: {{ MovieInfo.original_title ? MovieInfo.original_title :
                MovieInfo.original_name }}</h3>
            <!-- flags  -->
            <div class="p-b image flag" v-if="flagsArray.includes(MovieInfo.original_language)">
               <img :src="getImageFlag()" alt="">
            </div>
            <!-- original_language  -->
            <h4 class="p-b" v-else>Lingua:{{ MovieInfo.original_language }}</h4>
            <!-- vote  -->
            <div class="vote">
                <h4 class="p-b">Voto: </h4>
                
                    <i  v-for="n in getStar()" class="fa-solid fa-star active"></i>
                    <i v-for="n in 5 - getStar()" class="fa-regular fa-star "></i>

              
            </div>
            <!-- overview  -->
            <div class="wrapper-overview">
                  <h4>Overview</h4>
                  <div>{{ MovieInfo.overview }}</div>
            </div>
        </div>
        </div>
    </div>
</template>

<style scoped lang="scss">
  .single-card:hover .card .image-poster{
   display: none;
  }
  .single-card:hover .card{
    overflow: hidden;
  }
  .single-card:hover .wrapper-text{
    display: block;
  }
.single-card {
    color: white;
    position: relative;
    background-color: rgb(69, 66, 66);
    border: 1px solid black;
    box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px, rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px, rgba(0, 0, 0, 0.17) 0px 12px 13px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
    border-radius: 4px;
    width: calc((100% / 6) - 20px);
    margin: 10px;
    height: 430px;
     .card{
        width: 100%;
        height: 100%;
        .image-poster {
            height: 100%;
        img {

            object-fit: cover;
            width: 100%;
            height: 100%;
        }
      }
      .null {
            height: 100%;
        img {

            object-fit: cover;
            width: 100%;
            height: 50%;
            padding-bottom: 20px;
        }
      }


     }
      

     .wrapper-text{
         display: none;
         padding: 40px 5px 10px 5px;
    .image.flag {
        width: 10%;
        img {
            object-fit: cover;
            width: 100%;
            height: 20px;
        }
    }


    .vote {
        display: flex;
        justify-content: start;

        .active {
            color: #FFBD00;
        }
    }
     }
}

.p-b {
    padding-bottom: 10px;
}

</style>