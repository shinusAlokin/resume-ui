<template>
  <div class="container">
    <div class="left-container"></div>
    <div class="right-container">
      <Header title="Resumes" />
      <div class="search-addresume">
        <SearchBar placeholder="search by email or name" />
        <AddResume context="Add Resume"/>
      </div>
        <Listing />
        <Kebab />
    </div>
  </div>
</template>

<script>
import Header from "./components/Header.vue"
import Listing from "./components/Listing.vue"
import SearchBar from "./components/SearchBar.vue"
import AddResume from "./components/AddResume.vue"
import Kebab from "./components/Kebab.vue"

    export default{
      name: "App",
      post:"",
      components:{
        Header,
        Listing,
        SearchBar,
        AddResume,
        Kebab
      },
      // computed:{
      //   filterPost(){

      //   }
      // }
    }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50; */
}

.container{
  width: 100%;
  display: flex;
  align-items: center;
  flex-direction: row;
  justify-content: center;
}

.left-container{
  width: 16%;
}
.right-container{
  width: 100%;
  padding: 1em;
  margin-top: 10px;
  left: 30%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-direction: column;
}

.search-addresume{
  width: 100%;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  margin-top: 10px;
}

</style>
