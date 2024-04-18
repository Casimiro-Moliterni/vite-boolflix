<script>
import { store } from '../store.js';
export default{
    name:'Card',
    data(){
        return{
            store
        }
    },
    props: {
        MovieInfo: Object,
        SerieInfo:Object,
    },
    methods:{
        getImageUrl(name) {
                return new URL(`./https://image.tmdb.org/t/p/w342${name}`, import.meta.url).href;
            }
    }
}
</script>

<template>
   <div class="single-card" v-if="MovieInfo" >
     <h2>Film</h2>
    <div class="image-poster"><img :src="getImageUrl(MovieInfo.poster_path)" alt=""></div>
     <h3 class="p-b">Titolo: {{ MovieInfo.title}}</h3>
     <h3 class="p-b">Titolo Orginale: {{ MovieInfo.original_title }}</h3>
     <div class="p-b image flag" v-if="MovieInfo.original_language == 'en'" ><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT5RDOxgmvLN9giVa3zfP0poYAk2jqwTJvueQ&s" alt=""></div>
     <div class="p-b image flag" v-else-if="MovieInfo.original_language == 'fr'" ><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Flag_of_France.svg/1200px-Flag_of_France.svg.png" alt=""></div>
     <div class="p-b image flag" v-else-if="MovieInfo.original_language == 'it'" ><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQMAAADCCAMAAAB6zFdcAAAAKlBMVEX///8AkkbOKzfG4NAAizbwy83LECMkmlXRP0jOKTYAlEjJ4tPxztDLDSGog9TvAAABDUlEQVR4nO3Qhw2AQAwEsBDKU/dflylOCMkewTUSzqsS7t4TakpY5sjB+hwB/a+DrRMcOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw6+PHgBNBXVQ0m/YKMAAAAASUVORK5CYII=" alt=""></div>
     <h4 class="p-b" v-else>Lingua:{{ MovieInfo.original_language }}</h4>
     <h4 class="p-b">Voto: {{ MovieInfo.vote_average }}</h4>
   </div>
   <div class="single-card" v-else>
    <h2>Serie</h2>
    <div class="image-poster"><img :src="getImageUrl(SerieInfo.poster_path)" alt=""></div>
     <h3  class="p-b">Titolo: {{ SerieInfo.name}}</h3>
     <h3 class="p-b">Titolo Orginale: {{ SerieInfo.original_name }}</h3>
     <div class="p-b image flag" v-if="SerieInfo.original_language == 'en'" ><img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcT5RDOxgmvLN9giVa3zfP0poYAk2jqwTJvueQ&s" alt=""></div>
     <div class="p-b image flag" v-else-if="SerieInfo.original_language == 'fr'" ><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Flag_of_France.svg/1200px-Flag_of_France.svg.png" alt=""></div>
     <div class="p-b image flag" v-else-if="SerieInfo.original_language == 'it'" ><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAQMAAADCCAMAAAB6zFdcAAAAKlBMVEX///8AkkbOKzfG4NAAizbwy83LECMkmlXRP0jOKTYAlEjJ4tPxztDLDSGog9TvAAABDUlEQVR4nO3Qhw2AQAwEsBDKU/dflylOCMkewTUSzqsS7t4TakpY5sjB+hwB/a+DrRMcOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw4cOHDgwIEDBw6+PHgBNBXVQ0m/YKMAAAAASUVORK5CYII=" alt=""></div>
     <h4 class="p-b" v-else>Lingua:{{ SerieInfo.original_language }}</h4>
     <h4 class="p-b">Voto: {{ SerieInfo.vote_average }}</h4>
   </div>
</template>

<style scoped lang="scss">
    .single-card{
        color: white;
        position: relative;
        background-color:lightgray;
        text-align: center;
        border: 1px solid black;
        width: calc((100% / 5 ) - 10px);
        margin: 5px;
        .image.flag{
            width: 30%;
            margin: 0 auto;
           img{
            object-fit: cover;
            width: 100%;
            height: 50px;
           }
        }
        .image-poster{
           position: absolute;
           top: 0;
           left: 0;
            width: 100%;
            height: 100%;
            z-index: 0;
           img{
           
            object-fit: cover;
            width: 100%;
            height: 100%;
           }
        }
        h2,h3,h4{
            position: relative;
            z-index: 1;
        }
    }
    .p-b{
        padding-bottom: 10px;
    }
</style>