<template>
  <div id="app">
    <Header :reset="resetResult"
    @startSearch= startSearch
     />
    
    <Main v-if="results.movie.length > 0" type='movie' :list="results.movie" />
    <Main v-if="results.tv.length > 0" type='tv' :list="results.tv" />
    <Main v-if="results.movie.length === 0" type='popularMovie' :list="results.popularMovie" />
    <Main v-if="results.tv.length === 0" type='popularTv' :list="results.popularTv" />
      <!-- creo una pagina alternativa a main con v-if="results.tv.length === 0  -->
   
  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue'
import Main from './components/Main.vue'
/* import MainPopular from './components/MainPopular.vue' */
export default {
  name: 'App',
  components: {
    Header,
    Main,
},
data(){
  return{
        moviePopular:"https://api.themoviedb.org/3/movie/popular",
        apiUrl:"https://api.themoviedb.org/3/search/",
        apiKey: "54208a98ced9879b596671aca0f2b73b",
        language:"it-IT",
  
        results:{ 
            'movie':[],
            'tv':[],
            'popularMovie':[],
            'popularTv':[]
        }

  }
},
methods:{

  startSearch(obj){
    if(obj.type === 'all'){
      this.getApi(obj.text, 'movie')
      this.getApi(obj.text, 'tv')
    }else{
      this.getApi(obj.text, obj.type)
    }
    this.movie = this.startSearch
    console.log(this.movie)
  },

  resetResult(){
    this.results.movie = [];
    this.results.tv= [];
    this.results.all= [];
  },

   getApi(query, type){
     this.resetResult();
     axios.get(this.apiUrl+type,{
       params:{
         api_key: this.apiKey,
         query: query,
         language: this.language
       }
     })
    .then(res=> {
      this.results[type] = res.data.results;
      console.log(res.data);
    })
    .catch(err=> {
      console.log(err);
    })
   }
},
created(){
  axios.get("https://api.themoviedb.org/3/movie/popular",{
    params:{
        api_key: this.apiKey,
        language: this.language
    }
  })
  .then(res=> {
    this.results['popularMovie'] = res.data.results;
  })
  .catch(err=> {
    console.log(err);
  }),
  axios.get("https://api.themoviedb.org/3/tv/popular",{
    params:{
        api_key: this.apiKey,
        language: this.language
    }
  })
  .then(res=> {
    this.results['popularTv'] = res.data.results;
  })
  .catch(err=> {
    console.log(err);
  })
}
}

</script>

<style lang="scss">
@import '@/assets/style/general.scss';

</style>
