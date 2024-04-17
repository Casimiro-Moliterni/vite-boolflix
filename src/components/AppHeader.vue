<script>
import {store} from '../store.js'
export default {
    name:'AppHeader',
    data(){
        return{
            store
        }
    }
}
</script>

<template>
    <header>
        <h1>BOOLFIZ</h1>
        <nav>
        <input type="text" v-model="store.searchText"  >
        <button @click="$emit('searchPerfomed')">cerca</button>
    </nav>
    </header>
</template>

<style scoped lang="scss">
header{
    margin: 0 auto;
    padding: 15px;
    width: 90%;
    font-size: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    h1{
        color: red;
    }
    nav{

        display: flex;
        align-items: center;
        gap: 10px;
        input,button{
            padding: 10px;
            border-radius: 10px;
            font-size: inherit;
        }
    }
}
</style>