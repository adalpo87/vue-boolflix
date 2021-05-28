<template>

  <div class="text-center">

  <div class="poster"><img :src="getPoster(card)" alt=""></div>

  <h2>{{ card.title || card.name }}</h2>

  <h4>{{ card.original_title  || card.original_name}}</h4>

  <h5><img :src="flagLang(card)" :alt="card.title"></h5>

  <div class="star"><i v-for="index in Math.ceil(card.vote_average/2)" :key="index" class="fas fa-star"></i></div>

  </div>

</template>

<script>
import '@fortawesome/fontawesome-free/css/all.css'
import '@fortawesome/fontawesome-free/js/all.js'
export default {
 name: 'Card',
 props:{
     card: Object
 },
 data(){
   return{
     star: '<i class="fas fa-star"></i>'
   }
 },
 methods:{
     flagLang(card){
        let lang = card.original_language
        if(lang =='en'){
          lang='us'
        }
        return "https://www.countryflags.io/"+lang+ "/flat/64.png"
      },
      getPoster(card){
        let posterURL = card.poster_path;
        let sizePoster = "w342";
        return "https://image.tmdb.org/t/p/"+sizePoster+ posterURL;
      },
    
  }
}
</script>

<style lang="scss" scoped>
   div{

       .star{
           color: gold;
         }
        list-style: none;
     
   }
</style>