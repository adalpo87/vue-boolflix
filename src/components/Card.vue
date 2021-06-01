<template>

 <div class="main-card">
<!-- ------------------------------------------------- -->
<div class="flip-card">
  <div class="flip-card-inner">
    <div class="flip-card-front">
    <img v-if="card.poster_path !== null" class="poster" :src="getPoster(card)" :alt="card.title || card.name">
    <div v-if="card.poster_path === null">
    <h2>{{ card.title || card.name }}</h2>
    <p>Nazione:  <img :src="flagLang(card)" :alt="card.title"></p>
    <p v-if="card.vote_average !== 0" class="star">
         <i v-for="index in Math.ceil(card.vote_average/2)" :key="index" class="fas fa-star"></i>
         <i v-for="index in Math.floor(5-card.vote_average/2)" :key="index" class="far fa-star"></i>
       </p>
    </div>
    </div>
    <div class="flip-card-back">
       <h1 >{{ card.title || card.name }}</h1>
       <p>{{ card.original_title  || card.original_name}}</p>
       <p>{{ card.overview }}</p>
       <p>Nazione:  <img :src="flagLang(card)" :alt="card.title"></p>
       <p>{{card.vote_average/2}}</p>
       <p class="star">
         <i v-for="index in Math.ceil(card.vote_average/2)" :key="index" class="fas fa-star"></i>
         <i v-for="index in Math.floor(5-card.vote_average/2)" :key="index" class="far fa-star"></i>
       </p>
    </div>
  </div>
</div>

</div>

<!-- --------------------------------------------------->
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

 @import '@/assets/style/card.scss';
 
</style>