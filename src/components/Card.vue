<template>

  <div>
        <ul>
            <li>{{ card.title}}</li>
            <li>{{ card.original_title  || card.original_name}}</li>
            <li><img :src="flagLang(card)" :alt="card.title"></li>
            <li>{{ card.vote_average }}</li>
        </ul>
  </div>

</template>

<script>
export default {
 name: 'Card',
 props:{
     card: Object
 },

 methods:{
     flagLang(card){
        let lang = card.original_language
        if(lang =='en'){
          lang='us'
        }if(lang =='it'){
          lang ='it'
        }
        return "https://www.countryflags.io/"+lang+ "/flat/64.png"
      }
  }

}
</script>

<style lang="scss" scoped>
   div{
       margin: 20px;
       border: 1px solid black;
       ul{
           list-style: none;
       }
   }
</style>