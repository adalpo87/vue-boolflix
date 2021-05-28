<template>
  <header class="d-flex justify-content-sm-between container align-items-sm-center">
     <div class="d-flex justify-content-center align-items-center">
         <h1>BOOLFLIX</h1>
    </div>
    
 
  <div div class="">
      <div class="flex-grow-1 d-flex justify-content-center">
          <input 
          v-model.trim="textSearch"
          placeholder="Cerca film o serie tv"
          class="form"
          type="text" />
        
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'movie'})"
        class="ms-3">CERCA FILM</button>
        
        
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'tv'})"
        class="ms-3">CERCA SERIE</button>
      
       
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'all'})"
        class="ms-3">CERCA TUTTO</button>
              
      </div>
    </div>



  </header>
</template>

<script>
export default {
    name:'Header',
components:{

},
data(){
    return{
        textSearch: '',
    }
}
}
</script>

<style lang="scss" scoped>
 @import '@/assets/style/header.scss';
    
</style>