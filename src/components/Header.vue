<template>
  <header>
     
         <h1 @click="reset, resetText()">BOOLFLIX</h1>
    
    
 
 
      <div class="header-dp">
          <input 
          v-model.trim="textSearch"
          placeholder="Cerca film o serie tv"
          class="form"
          type="text" />
        
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'movie'}),resetText()"
        class="ms-3">CERCA FILM</button>
        
         
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'tv'}),resetText()"
        class="ms-3">CERCA SERIE</button>
      
       
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'all'}),resetText()"
        class="ms-3">CERCA TUTTO</button>
              
      </div>
   



  </header>
</template>

<script>
export default {
    name:'Header',
components:{

},
props:{
  reset: Function
},
data(){
    return{
        textSearch: '',
    }
},
methods:{
  resetText(){
    let reset = '';
    this.textSearch = reset;
    return this.textSearch 
  }
}
}
</script>

<style lang="scss" scoped>
 @import '@/assets/style/header.scss';
    
</style>