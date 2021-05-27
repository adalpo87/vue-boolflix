<template>
  <div id="app">
    <Header
    @startSearch= startSearch
     />
    <Main v-if="results.movie.length > 0" type='movie' :list="results.movie" />
    <Main v-if="results.tv.length > 0" type='tv' :list="results.tv" />
    <Main v-if="results.all.length > 0" type='all' :list="results.all" />

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
        apiUrl:"https://api.themoviedb.org/3/search/",
        apiKey: "54208a98ced9879b596671aca0f2b73b",
        language:"it-IT",
  
        results:{ 
            'movie':[],
            'tv':[],
            'all':[]
        }
  }
},
methods:{

  startSearch(obj){
    this.resetResult();
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
  
},
}

</script>

<style lang="scss">
@import '@/assets/style/general.scss';
</style>
