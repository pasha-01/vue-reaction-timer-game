<template>
   <p>Time of Reaction: {{ score }} ms </p>
   <p class="rank">{{ rank }}</p>
</template>

<script>
import { readonly } from 'vue'

export default {
    props:['score'],
    data(){
        return{
            rank : null,
        }
    },
    mounted(){
        if(this.score<250){
            this.rank = 'Fast Rabit'
        }
        else if(this.score<450){
            this.rank="Rapid action"
        }
        else{
            this.rank= " Too Slow"
        }
    },

}
</script>

<style>
.rank{
    font-size: 1.5rem;
    color: green;
    font-weight: bold;
}
</style>