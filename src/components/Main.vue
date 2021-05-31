<template>
<main>
    <h1>{{titles[type]}}</h1>
     <span> {{ list.length }} </span> 
    <div class="main-c">
    <Card
    v-for="poster in list" :key="poster.id"
    :card="poster"
    />
    </div>
</main>
</template>

<script>
import Card from '@/components/Card';
export default {
    name: 'Main',
    components:{
        Card,
    },
    props:{
        type: String,
        list: Array
    },
data(){
    return{
        titles:{
            'movie': 'Film trovati:',
            'tv': 'Serie TV trovate:',
            'popularMovie': 'I film del momento:',
            'popularTv': 'Serie TV del momento:'
        }
    }
}
}
</script>

<style lang="scss" scoped>
 @import '@/assets/style/main.scss';   

</style>