<template>
  <div id="app">
    <Header @searchMovie= "this.searchMovies"/>
    <Main 
      v-for= "movie in movies" :key= "movie.id"
      :movie = movie
    />

  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'
export default {
  name: 'App',
  components: {
    Header,
    Main,
},
data(){
  return{
        apiUrl:"https://api.themoviedb.org/3/search/movie",
        apiKey: '4df959eab3283b1ac2c5a67b1e5247b9',
        query:"",
        language:"it-IT",
        movies:[]
  }
},
methods:{
  searchMovies(query){
      this.query = query;
        axios.get(this.apiUrl,{
          params:{
                  api_key: this.apiKey,
                  query: this.query,
                  language: this.language
                 }
        })
      .then(resp => {
            this.movies = resp.data.results;
            console.log(this.movies);
        })
      .catch(err => {
            console.log(err);
        })
      }
    }
}

</script>

<style lang="scss">
@import '@/assets/style/general.scss';
</style>
