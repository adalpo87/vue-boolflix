<template>
  <header>
     <div class="d-flex justify-content-center align-items-center">
         <h1>BOOLFLIX</h1>
    </div>
    
 
  <div div class="container d-flex pt-3">
      <div class="flex-grow-1 d-flex justify-content-center">
          <input 
          v-model.trim="textSearch"
          placeholder="Cerca..."
          class="form"
          type="text" />
        
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'movie'})"
        class="btn btn-primary ms-3">CERCA FILM</button>
        
        
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'tv'})"
        class="btn btn-primary ms-3">CERCA SERIE</button>
      
       
        <button 
        @click="$emit('startSearch',{text:textSearch, type:'all'})"
        class="btn btn-primary ms-3">CERCA TUTTO</button>
              
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
    header{
        div{
            h1{
                color: red;
                font-size: 4rem;
            }
        }
    }
</style>