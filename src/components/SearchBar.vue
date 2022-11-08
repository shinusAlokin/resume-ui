<template>
    <section class="search-container search-listing-page"> 
        <input type="text" v-model="search" :placeholder="placeholder">
    </section>
</template>

<script>

import Listing from './Listing.vue'
    export default{
        name:"SearchBar",
        props:{
            placeholder: String,
            value: String
        },
        components:{
            Listing,
        },
        data(){
            return{
                search: ''
            }
        }
    }
</script>
<style>
    input{
        width: 300px;
        height: 30px;
        padding: 0.5em;
    }
</style>

