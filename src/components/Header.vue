<template>
    <header>
        <h1>{{title}}</h1>
        <!-- <hr> -->
    </header>
</template>

<script >
    export default{
        name:'Header',
        props:{
            title: String,
        },
    } 
</script>

<style scoped>
    /* header{
        display: flex;
        justify-content: flex-start;
        align-items: flex-start;
    }
    hr{
        border-bottom: 1px solid #333;
    } */
</style>