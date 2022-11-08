<template>
    <div class="add-resume-listingpage">
        <i class="fas fa-plus"></i>
        <a href="">{{context}}</a>
    </div>
</template>

<script>
    export default{
        name: "AddResume",
        props:{
            context:String
        }
    }
</script>

<style>

    .add-resume-listingpage{
        color: teal;
        float: right;
        font-size: 0.8rem;
        padding: 5px;
    }
    .add-resume-listingpage  a{
        text-decoration: none; 
        color: teal;
    }
</style>