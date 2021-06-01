<template>
  <input type="text" v-model="searchTerm"> 
  <select v-model="searchType">
    <option value="movie">Movies</option>
    <option value="series">Series</option>
    <option value="episode">Episode of a serie</option>
  </select>
  <button @click="searchDB">Click to Search</button>
  <movieList v-bind:movieDetails="this.searchResults"/>
</template>

<script>
import movieList from "./components/movieList"
import axios from 'axios'

export default {
  name: 'App',
  data(){
    return {
      searchTerm: '',
      searchType: '',
      searchResults: {}
    }
  },
  components: {
    movieList
  },
  methods : {
    searchDB() {
      axios.get('http://www.omdbapi.com/', {
        params: {
          apikey: '17e4e4d0',
          s: this.searchTerm,
          type: this.searchType
        }
      })
            .then((response) => {
              console.log(response.data.Search);
              this.searchResults = response.data.Search;
            })
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
