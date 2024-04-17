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
        {{ store.test }}
    </header>
</template>

<style scoped lang="scss">
</style>