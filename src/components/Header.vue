<template>
  <header>
     <div class="d-flex justify-content-center align-items-center">
         <h1>BOOLFLIX</h1>
    </div>
    <div class="text-center mt-5">
        <input 
        v-model.trim= "searchMovie"
        type="text">
        <button 
        @click.prevent="$emit('searchMovie',searchMovie)"
        class="ms-4">INVIA</button>
    </div>
  </header>
</template>

<script>
export default {
    name:'Header',
data(){
    return{
        searchMovie: "",
    }
}
}
</script>

<style lang="scss" scoped>
    header{
        height: 300px;
        div{
            height: 30%;
            h1{
                color: red;
            }
        }
        
    }
</style>