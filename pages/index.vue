<template>
   <div id="app">
      <h3>Welcome to the Paper-Searcher | An experimental challenge for the day. </h3>
      <SearchBar v-on:newSearch="searchChanged"></SearchBar>
  </div>
</template>

<script>
import axios from 'axios';
  import SearchBar from "~/components/SearchBar.vue";
  const API_KEY = "cde616a7d0b956c3f58a2542ba740e06"; //API Key for ScienceDirect

  export default {
    name: 'app',
    components: {
      SearchBar
    },
    methods: {
        searchChanged: function(querySearch)
        {
          console.log("In the function!");
          axios.get("https://api.elsevier.com/content/search/scidir", {
            headers: {
              'Access-Control-Allow-Origin': '*',
              'Access-Control-Allow-Headers': 'Origin, X-Requested-With, Content-Type, Accept',
              'content-type': 'application/x-www-form-urlencoded' 
            },
            params: {
            query: querySearch,
            apiKey: API_KEY
          }
          }).then(function(response){
            console.log(response);
          })
          .catch(function(error){
            console.log(error);
          })
        }
    }
  }

</script>

<style>
</style>

