<script>
export default{
    name:'Card',
    props: {
        MovieInfo: Object,
    }
}
</script>

<template>
   <div class="single-card">
     <div class="image">
        <img src="" alt="">
     </div>
     <h3 class="p-b">{{ MovieInfo.title}}</h3>
     <div class="p-b">{{ MovieInfo.original_title }}</div>
     <div class="p-b">{{ MovieInfo.original_language }}</div>
     <div class="p-b">{{ MovieInfo.vote_average }}</div>
   </div>
</template>

<style scoped lang="scss">
    .single-card{
        text-align: center;
        border: 1px solid black;
        width: calc((100% / 5 ) - 10px);
        margin: 5px;
    }
    .p-b{
        padding-bottom: 10px;
    }
</style>