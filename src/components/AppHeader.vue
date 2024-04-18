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
        <div class="wrapper-header">
           <h1>BOOLFIZ</h1>
          <nav>
            <input type="text" v-model="store.searchText"  >
            <button @click="$emit('searchPerfomedMovie')">cerca</button>
          </nav>
        </div>
    </header>
</template>

<style scoped lang="scss">
header{
    padding: 15px;
    font-size: 20px;
    background-color: black;
   .wrapper-header{
    width: 90%;
    margin: 0 auto;
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
            border-radius: 5px;
            font-size: inherit;
            border: none;
            cursor: pointer;
        }
    }
   }
}
</style>