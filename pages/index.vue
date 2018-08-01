<template>
   <div id="app">
      <h3>Welcome to the Paper-Searcher | An experimental challenge for the day. </h3>
      <SearchBar v-on:newSearch="searchChanged"></SearchBar>
      <PaperList></PaperList>
  </div>
</template>

<script>
import axios from 'axios';
  import SearchBar from "~/components/SearchBar.vue";
  import PaperList from "~/components/PaperList.vue";
  import PaperListItem from "~/components/PaperListItem.vue"
  const API_KEY = "cde616a7d0b956c3f58a2542ba740e06"; //API Key for ScienceDirect
  const searchResult= "search-result";
  
  export default {
    name: 'app',
    components: {
      SearchBar,
      PaperList,
      PaperListItem
    },
    data() {
      return { papers: [] };
    },
    methods: {
        searchChanged: function(querySearch)
        {
          console.log("In the function!");
          axios.get("https://api.elsevier.com/content/search/scidir", {
            headers: { //To allow CORS. TODO: Fix it. 
              'Access-Control-Allow-Origin': '*',
              'Access-Control-Allow-Headers': 'Origin, X-Requested-With, Content-Type, Accept',
              'content-type': 'application/x-www-form-urlencoded' 
            },
            params: {
            query: querySearch,
            apiKey: API_KEY
          }
          }).then(function(response){
            console.log(response.data);
            // this.papers=response.data.searc;
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

